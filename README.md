
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Evaluation of Competing Risks Prediction Models using Polytomous Discrimination Index

<!-- badges: start -->
<!-- badges: end -->

For competing risks data, it is often important to predict a patient’s
outcome status at a clinically meaningful time point after incorporating
the informative censoring due to competing risks. This can be done by
adopting a regression model that relates the cumulative incidence
probabilities to a set of covariates. To assess the performance of the
resulting prediction tool, we propose an estimator of the polytomous
discrimination index applicable to competing risks data, which can
quantify a prognostic model’s ability to discriminate among subjects
from different outcome groups. The proposed estimator allows the
prediction model to be subject to model misspecification and enjoys
desirable asymptotic properties. We also develop an efficient
computation algorithm that features a computational complexity of
*O*(*n*log *n*). A perturbation resampling scheme is developed to
achieve consistent variance estimation. Numerical results suggest that
the estimator performs well under realistic sample sizes. We apply the
proposed methods to a study of monoclonal gammopathy of undetermined
significance. \[1\]

## Installation

You can install the development version of CRPDI like so:

``` r
library(devtools)
install_github("lilyxj91/CRPDI",force = TRUE)
```

## Example

This is a basic example of computing PDI with competing risks data using
Fine-Gray model.

``` r
library(CRPDI)
data(example_data)
n_l = 3  # number of outcome categories
tau = 1.4 # prespecified time for prediction

PDIs = fine_gray_pdi( dat=example_data, tau=tau, n_l=n_l, seed=1, cv_rep=3, zcov=c("z1","z2") )
PDIs
#> $pdi_specific
#> [1] 0.6294670 0.5824985 0.5620825
#> 
#> $pdi_overall
#> [1] 0.5913493
```

## Reference

\[1\] Ding, M., Ning, J., & Li, R.. (2020). Evaluation of competing
risks prediction models using polytomous discrimination index. Canadian
Journal of Statistics. <https://doi.org/10.1002/cjs.11583>
