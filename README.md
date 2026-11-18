# Problem-Set-4
Store Revenue Model

## Problem

An inherited model claimed to be validated with R² near 0.94, yet it over-forecast large stores. I checked what that score measured and whether the model could predict stores it had not seen.

## Finding

The all-data OLS fit had R² = 0.9267, but held-out R² was 0.9151. The straight-line model missed how revenue growth flattens with floor area. On held-out data, it over-forecast the largest fifth of stores by $23.9k per month on average. A separate validation example showed that selecting features before cross-validation can inflate R²: 0.09 on pure noise versus −0.152 when selection is fitted within each fold.

The selected model uses area, traffic, income, years open, and area squared. Nested cross-validation estimated RMSE of $61.4k per store-month. This estimate applies to new stores from the same simulated process; it has not been tested on future months.

## Method

I simulated 500 stores, fitted and diagnosed the inherited OLS model, compared training and held-out errors, and used residual plots and VIFs to investigate its failures. I compared models of increasing complexity, selected one with five-fold cross-validation, and estimated its error with nested cross-validation. A learning curve checked whether more stores or a better model was likely to help. The next check should use actual store-by-month data with later months held out.
