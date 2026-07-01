## Overview
Rather than relying on static TDEE formulas, this project treats TDEE estimation as
a data-driven numerical problem:

- **Interpolation** — fills missing weight/calorie entries using linear and cubic
  spline methods, with error comparison (MAE/RMSE) to justify method selection
- **Phase Detection** — identifies bulk/cut phases via polynomial curve fitting and
  numerical differentiation (5-point stencil) to find slope sign changes
- **Piecewise Regression** — fits least-squares regression (solved via normal
  equations) to each detected phase to estimate weight trend and back-calculate TDEE
- **Nonlinear Curve Fitting** — fits a curved model across the full trajectory to
  capture the smooth, non-linear nature of weight change (accounting for adaptive TDEE)

## Methods Used
- Linear & cubic spline interpolation
- BIC-based polynomial degree selection
- Numerical differentiation (finite difference)
- Least-squares regression (normal equations)
- Piecewise regression across phase segments
- Nonlinear curve fitting