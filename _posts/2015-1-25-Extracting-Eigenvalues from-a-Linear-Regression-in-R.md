The function below extracts the eigenvalues and an eigenvector from a linear regression model. I wrote this function so that the eigenvalues and vectors are the same as those reported by the SAS PROC REG procedure when using the COLLIN option.
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
