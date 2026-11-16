# econ3916-lab16-regularization
# Regularization: Buying Bias to Sell Variance

## Objective
I compared OLS, LASSO and Ridge on a simulated design with far more predictors than real signal, to see what a penalty gives up and what it gains.

## Methodology
- Built a design with 200 predictors, only 5 of them real, and 105 training rows, then fitted OLS, LASSO and Ridge to it.
- Traced the LASSO path to see where the true predictors and the first noise variable entered.
- Chose the LASSO penalty by 5-fold cross-validation, with the scaler fitted inside every fold.
- Scored LASSO's selection against the known truth.
- Gave LASSO and Ridge two near-duplicate predictors that both mattered, and compared how each handled them.
- Wrote my own prompt asking an AI for the cross-validation loop and checked its penalty and CV MSE against my own.

## Key Findings
- Test MSE was 12.9587 for OLS, 10.1128 for Ridge and 1.4219 for LASSO. OLS fit the training rows perfectly and failed on new ones.
- On the LASSO path, all five true predictors were in from step 6, and the first noise variable entered at step 17.
- Cross-validation with the scaler fitted inside each fold chose lambda 0.1995, with a CV MSE of 1.5502.
- LASSO found 5 of the 5 true predictors, along with 11 false positives.
- With two near-duplicate predictors, LASSO put 4.462 on one and zero on the other, while Ridge split the weight 1.618 and 1.609.
- My prompt took 2 rounds. The AI's loop matched my lambda and CV MSE in every digit in both rounds; in the second round I removed a solver setting it had added without being asked.
