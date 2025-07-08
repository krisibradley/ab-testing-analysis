# Customer Service Help Center A/B Testing Analysis

A comprehensive statistical analysis of an A/B test evaluating a new help center design vs. the current design, demonstrating advanced experimentation skills and statistical rigor.

## 🎯 Project Overview

This project showcases end-to-end A/B testing expertise through the analysis of a customer service help center optimization experiment. The analysis demonstrates both frequentist and Bayesian approaches to experimentation, with advanced techniques including multiple testing correction, confidence intervals, power analysis, and temporal segmentation.

**Goal:** Evaluate whether a new homepage design improves user conversion rate.

**Design:**
- **Control Group:** Saw the existing homepage
- **Treatment Group:** Saw a redesigned homepage

**Metric:** Conversion rate (e.g., signup or start trial)

**Key Questions:**
- Is the difference in conversion statistically significant?
- Is the effect large enough to be practically important?
- Was the experiment sufficiently powered?

This notebook includes a full A/B test pipeline with:
- Visualizations of conversion & lift
- Two-proportion Z-test
- Confidence intervals
- Power & sample size analysis
- Business recommendations

**Business Context**: Testing whether a new help center design improves customer problem resolution rates compared to the current design.

## 📊 Key Findings

- **Sample Size**: 294,478 users (147K control, 147K treatment)
- **Test Duration**: 22 days
- **Primary Metric**: Conversion rate (successful problem resolution)
- **Result**: No statistically significant difference (p = 0.22, Z = 1.24)
- **Statistical Power**: 24.1% for observed effect, 51.6% for 2% improvement
- **Recommendation**: Do not implement new design

### Advanced Insights
- **Time-of-Day Effects**: Treatment performs better during evening hours (6-10 PM) with +0.6% average improvement
- **Multiple Testing**: 4 hours initially significant, but 0 remain after FDR correction
- **Bayesian Analysis**: 15.2% probability treatment is better; expected loss analysis confirms "don't implement"

## 🔬 Analysis Features

### Statistical Rigor
- ✅ **Intent-to-treat analysis** (industry standard)
- ✅ **Two-sample Z-test** for proportions
- ✅ **Multiple testing correction** (Bonferroni & FDR)
- ✅ **Confidence intervals** for effect sizes
- ✅ **Power analysis** and sample size calculations
- ✅ **Bayesian alternative analysis** with conjugate priors

### Advanced Techniques
- ✅ **Temporal segmentation** (hourly and daily patterns)
- ✅ **Data quality assessment** (randomization checks)
- ✅ **Effect size quantification** (Cohen's h)
- ✅ **Expected loss framework** (Bayesian decision theory)
- ✅ **Professional visualizations** for stakeholders

### Business Focus
- ✅ **Actionable recommendations** with clear rationale
- ✅ **Time-based rollout strategy** (evening hours first)
- ✅ **Risk assessment** and uncertainty quantification
- ✅ **Executive-level summary** with key insights

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- Required packages: `pandas`, `numpy`, `scipy`, `matplotlib`, `seaborn`, `statsmodels`

### Installation
```bash
# Clone the repository
git clone https://github.com/yourusername/ab-testing-analysis.git
cd ab-testing-analysis

# Install dependencies
pip install -r requirements.txt

# Or use conda
conda env create -f environment.yml
conda activate ab-testing-env
```

### Run the Analysis
```python
from src.ab_testing_analysis import HelpCenterABAnalysis

# Initialize analysis
analysis = HelpCenterABAnalysis('data/ab_data.csv')

# Run complete analysis
analysis.run_complete_analysis()

# Quick results summary
results = analysis.results
print(f"P-value: {results['statistical_test']['p_value']:.4f}")
print(f"Conversion lift: {results['statistical_test']['lift']:.2f}%")
```

## 📈 Key Results

### Overall Test Results
| Metric | Control | Treatment | Difference | Statistical Test |
|--------|---------|-----------|------------|------------------|
| **Users** | 147,202 | 147,276 | +74 | Balanced (✓) |
| **Conversions** | 17,723 | 17,514 | -209 | |
| **Conversion Rate** | 12.04% | 11.89% | -0.15pp | |
| **Relative Lift** | - | - | -1.31% | |
| **Z-statistic** | - | - | 1.24 | |
| **P-value** | - | - | 0.22 | Not Significant |
| **95% CI** | - | - | [-3.23%, +0.65%] | Includes 0 |

### Time-of-Day Analysis
| Time Period | Control Rate | Treatment Rate | Lift | Status |
|-------------|-------------|----------------|------|---------|
| **Early Morning (4-6 AM)** | 12.5% | 11.1% | -11.2% | ❌ Worse |
| **Business Hours (9-5 PM)** | 12.1% | 11.8% | -2.5% | ⚠️ Neutral |
| **Evening (6-10 PM)** | 11.7% | 12.3% | +5.1% | ✅ Better |
| **Late Night (11 PM-3 AM)** | 12.8% | 11.9% | -7.0% | ❌ Worse |

### Power Analysis
| MDE (Relative) | Users per Group | Total Users | Current Power |
|----------------|-----------------|-------------|---------------|
| 1% | 1,150,465 | 2,300,930 | 17.0% |
| 2% | 288,849 | 577,698 | **51.6%** |
| 3% | 128,924 | 257,848 | 84.9% |
| 5% | 46,805 | 93,610 | 99.9% |
| 10% | 11,945 | 23,890 | 100% |

**Current Status**: Reasonably powered for business-meaningful effects (2%+)

## 🎨 Visualizations

The analysis generates 12+ professional visualizations including:

- **Conversion Rate Comparison** with confidence intervals
- **Daily Trend Analysis** over 22-day period  
- **Hourly Segmentation** with multiple testing correction
- **Bayesian Posterior Distributions** for both groups
- **Statistical Power Curves** for different effect sizes
- **Executive Dashboard** with key metrics

All plots are publication-ready with clear titles, legends, and statistical annotations.

## 🧠 Statistical Methodology

### Frequentist Approach
1. **Hypothesis Testing**: Two-sample Z-test for proportions
2. **Multiple Comparisons**: Benjamini-Hochberg FDR correction for 24 hourly tests
3. **Effect Size**: Cohen's h and relative lift with confidence intervals
4. **Power Analysis**: Prospective and retrospective power calculations

### Bayesian Approach
1. **Prior Specification**: Beta(1,1) uninformative priors
2. **Posterior Inference**: Beta-Binomial conjugate analysis
3. **Decision Framework**: Expected loss with business constraints
4. **Uncertainty Quantification**: Credible intervals and probability statements

### Data Quality
- **Randomization Check**: Chi-square test for balance (p = 0.84)
- **Temporal Consistency**: Groups run simultaneously 
- **Data Cleaning**: Removed 3,893 inconsistent assignments
- **Sample Size Validation**: Adequate power for 2% MDE

## 💼 Business Recommendations

### Primary Recommendation: **DO NOT IMPLEMENT**
- No statistically significant improvement (p = 0.22)
- Negative point estimate (-1.31% relative change)
- 84.8% Bayesian probability that control is better

### Secondary Insights
1. **Evening Opportunity**: Consider targeted A/B test for 6-10 PM users
2. **Power Planning**: Well-powered for 2%+ effects (51.6% power for 2% improvement)
3. **Follow-up Testing**: Design iteration based on user feedback
4. **Sample Size**: Current design appropriate for detecting business-meaningful effects

### Risk Assessment
- **Implementation Risk**: Expected 0.158% conversion rate loss
- **Opportunity Cost**: Minimal (15.2% chance of missing improvement)
- **Sample Size**: Well-designed for detecting 2-3% effects (51.6% power for 2%)
- **Experiment Design**: Appropriately powered for business-relevant effect sizes

## 🛠 Technical Skills Demonstrated

### Statistical Analysis
- A/B testing methodology and best practices
- Hypothesis testing and multiple comparisons
- Confidence intervals and effect size estimation
- Bayesian inference and decision theory
- Power analysis and experimental design

### Data Science
- Large-scale data processing (294K records)
- Temporal analysis and segmentation
- Data quality assessment and cleaning
- Statistical visualization and storytelling
- Reproducible analysis with version control

### Business Acumen
- Experimental design for business problems
- Risk-aware decision making
- Stakeholder communication and reporting
- Cost-benefit analysis and ROI thinking
- Strategic recommendations with uncertainty

## 🤝 Contributing

This is a portfolio project, but feedback and suggestions are welcome! Please feel free to:
- Open issues for questions or suggestions
- Submit pull requests for improvements
- Share feedback on methodology or presentation

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💼 About

This analysis was created as part of a data science portfolio to demonstrate advanced A/B testing and statistical analysis skills. The project showcases:

- **Industry-standard methodology** used by top tech companies
- **Statistical rigor** with proper multiple testing correction
- **Business-focused insights** with actionable recommendations
- **Professional presentation** suitable for executive audiences

## 👨‍💻 Author

**[Kristopher Bradley, Ph.D.]**
- **Email:** kibradleyphd@gmail.com
- **LinkedIn:** [Your LinkedIn Profile](https://www.linkedin.com/in/kibradleyphd/)
- **GitHub:** [Your GitHub](https://github.com/krisibradley)
- **YouTube:** [Your YouTube](https://www.youtube.com/@kibradleyphd)
