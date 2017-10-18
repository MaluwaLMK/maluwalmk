The function below extracts the eigenvalues and an eigenvector from a linear regression model. I wrote this function so that the eigenvalues and vectors are the same as those reported by the SAS `PROC REG` procedure when using the `COLLIN` option.

```r
scaleEigen <- function(fit){
 # Calculate the eigenvalues and eigenvectors
 #
 # args: fit - an object of the lm or glm class from which you would
 #             like to extract the X matrix
 #
 # Output: eigenvalues and eigenvectors of the X'X matrix
 #
 # Method:
 #         fit <- lm(y ~ x1 + x2 + x3, data = dataset)
 #         summary(fit)
 #         scaledEigen(fit)
 #
 model.data <- fit$model  # The data used in the regression
 Xvec <- as.matrix(cbind(1, model.data[,-1]))  # X matrix including intercept
 Xvec <- apply(Xvec, 2 , function(x) x/sqrt(sum(x^2)))  # Rescale the X matrix
 eigenValues <- eigen(t(Xvec)%*%Xvec)
 return(eigenValues)
}
```

For example, using cars data from the R dataset package we can extract eigenvalues and eigenvectors of a **X\'X** matrix which can be used to assess multicollinearity of regressors in a linear regression.

```r
data(cars)
cars.lm <- lm(dist ~ speed, data = cars)
summary(cars.lm)
 
# Extract the eigenvalues and eigenvectors from cars.lm using
# the function scaleEign above
scaleEigen(cars.lm)
```

This produces the eigenvalues and their associated eigenvectors of a class `list` as shown in the R output below.

```
$values
[1]    1.94680083          0.05319917

$vectors
[,1]                            [,2]
[1,]  -0.7071068          0.7071068
[2,]  -0.7071068        -0.7071068
```

You can also assign the output to a an object and access the values using the dollar sign as below:

```r
eigenV <- scaleEigen(cars.lm) 
eigenV$values  # Eigenvalues
eigenV$vectors  # Eigenvectors
```

In a regression analysis, if there is one or more small eigenvalues of the **X\'X**, matrix it implies there are near-linear relationships (dependencies) among regressors and we may have multicollinearity issues in the analysis.

