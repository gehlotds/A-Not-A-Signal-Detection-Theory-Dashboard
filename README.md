# SDT Dashboard - A-Not A Signal Detection Analysis

A comprehensive R Shiny dashboard for conducting Signal Detection Theory (SDT) analysis on A-Not A discrimination tests using a 6-point rating scale. This tool implements Unequal Variance Maximum Likelihood Estimation and provides detailed statistical analysis for sensory discrimination studies.

## Features

- **Interactive Data Entry**: Easy-to-use grid interface for entering frequency data
- **Unequal Variance Model**: Implements corrected UEV MLE methodology matching SDT Assistant standards
- **Comprehensive Analysis**: Calculates da (sensitivity), AUC, criteria locations, and model fit statistics
- **Real-time Visualization**: Interactive ROC curves and SDT distribution plots using Plotly
- **Example Data**: Pre-loaded with Green & Swets (1966) benchmark data for validation
- **Parameter Guidelines**: Detailed interpretation guidelines for all SDT parameters
- **Model Validation**: Built-in validation against established SDT Assistant benchmarks

## Installation

### Prerequisites

Ensure you have R (version 4.0+ recommended) installed on your system.

### Required R Packages

```r
# Install required packages
install.packages(c("shiny", "DT", "plotly", "dplyr", "htmlwidgets", "numDeriv"))
```

### Running the Application

1. Clone this repository:
```bash
git clone https://github.com/yourusername/sdt-dashboard.git
cd sdt-dashboard
```

2. Open R/RStudio and run:
```r
# Load required libraries
source("app.R")  # This will launch the Shiny app
```

3. The application will open in your default web browser.

## Usage

### Basic Workflow

1. **Data Entry**: Enter your frequency data in the 6-point rating table
   - S1 = responses when 'Not A' was presented (noise trials)
   - S2 = responses when 'A' was presented (signal trials)
   - Higher numbers = higher confidence in 'A' responses

2. **Load Example Data**: Click "Load Example Data" to use Green & Swets (1966) benchmark data

3. **Run Analysis**: Click "Run SDT Analysis (UEV)" to perform the analysis

4. **Interpret Results**: View comprehensive results including:
   - Sensitivity measures (da)
   - ROC curve analysis
   - Model fit statistics
   - Interactive visualizations

### Data Format

The application expects frequency data in a 2x6 matrix format:

```
        Rating 1  Rating 2  Rating 3  Rating 4  Rating 5  Rating 6
S1        174      172       104       92        41        8
S2         46       57        66      101       154      173
```

## Technical Details

### Signal Detection Theory Implementation

- **Model**: Unequal-Variance Normal (UEV: YN LR/Beta)
- **Estimation**: Simultaneous Maximum Likelihood Estimation of all parameters
- **Parameters**: 7 total (5 criteria + intercept + slope)
- **Optimization**: Multi-method approach (Nelder-Mead + L-BFGS-B)

### Key Calculations

- **Sensitivity (da)**: `da = intercept / √((1 + slope²) / 2)`
- **AUC**: Trapezoidal integration of ROC curve
- **Goodness of Fit**: Chi-square (Pearson & Likelihood Ratio), AIC, BIC

### Validation

Results are validated against SDT Assistant benchmarks using Green & Swets (1966) data:
- Expected da: 1.239
- Expected intercept: 1.072  
- Expected slope: 0.7058

## Output Interpretation

### Primary Metrics

- **da (UEV)**: Sensitivity measure for Unequal Variance model
- **AUC**: Area Under the ROC Curve (0.5 = chance, 1.0 = perfect)
- **Criterion (c)**: Decision bias measure
- **Hit Rate**: P(Say 'A' | A presented)
- **False Alarm Rate**: P(Say 'A' | Not A presented)

### Model Fit Statistics

- **Chi-square tests**: Goodness of fit measures
- **p-values**: Model adequacy (p > 0.05 indicates good fit)
- **AIC/BIC**: Information criteria for model comparison
- **Convergence**: Optimization success indicator

## Dependencies

```r
shiny         # Web application framework
DT            # Interactive data tables
plotly        # Interactive plotting
dplyr         # Data manipulation
htmlwidgets   # HTML widget framework
numDeriv      # Numerical derivatives
```

## File Structure

```
sdt-dashboard/
│
├── app.R                 # Main Shiny application
├── README.md            # This file
└── LICENSE              # License file (if applicable)
```

## Contributing

Contributions are welcome! Please feel free to submit issues, feature requests, or pull requests.

### Development Guidelines

- Follow existing code style and commenting patterns
- Test with Green & Swets benchmark data
- Ensure all new features include appropriate documentation
- Validate statistical implementations against established references

## Citation

If you use this tool in your research, please consider citing:

```
Green, D. M., & Swets, J. A. (1966). Signal detection theory and psychophysics. Wiley.
```

## License

[Include your chosen license here - MIT, GPL-3, etc.]

## Acknowledgments

- Based on Signal Detection Theory principles from Green & Swets (1966)
- Validated against SDT Assistant methodology
- Implements statistical methods from sensory evaluation literature

## Contact

gehlotds1995@gmail.com

---

## Troubleshooting

### Common Issues

1. **Installation Problems**: Ensure all required packages are installed
2. **Data Import Issues**: Check that data follows the expected 2x6 format
3. **Analysis Errors**: Verify that both S1 and S2 contain non-zero values
4. **Performance**: Large datasets may require additional processing time

### Getting Help

- Check the Parameter Estimate Guidelines section in the app
- Review the built-in help text and tooltips
- Submit issues via GitHub Issues tab

  ## For more information, please download the PDF Additional Information
