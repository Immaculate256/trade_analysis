# The Evolving Nature of Global Trade: An Analysis of Time Varying Volatility, Conditional Correlations and Elasticities (1990- 2024)
This repository contains code and documentation for an empirical analysis of global trade patterns using World Development Indicators (WDI) data from 1990 to 2024. The study examines structural changes in trade and GDP linkages, volatility dynamics, and cross-country heterogeneity in crisis resilience.

## Scope and Objectives

The analysis addresses the following questions:
1. Has the relationship between trade openness and GDP growth changed after the 2008 Global Financial Crisis (GFC)?
2. How have trade and GDP volatility evolved over time, and what is their persistence?  
3. Do countries with service dominant export structures experience different crisis impacts than goods dominant economies?  
4. Is there a threshold level of trade openness associated with greater macroeconomic stability?  
5. Which countries consistently deviate from the global trade GDP relationship, and what does this imply about integration models?

## Data
-Source: World Bank World Development Indicators (WDI)  
-Coverage: 213 countries, annual frequency, 1990–2024  
-Final analytic sample: 7,455 country-year observations after listwise deletion of missing values  

-Key variables:  

 -gdp_growth: Annual real GDP growth (%)
 -goods_exports_usd, service_exports_usd: Nominal export values (USD)
 -trade_openness_pct`: (Goods + Services exports) / GDP × 100  
 -Derived series: log returns, service shares, ICT contributions, residuals

## Methods

All analyses implemented in Python 3.9. Key methodological steps include:
-Structural break detection: Chow test confirms 2008 as a significant break point in trade-GDP dynamics.
-Stationarity testing: Augmented Dickey Fuller (ADF) and KPSS tests applied; variables transformed (log, IHS) as needed.
-Volatility modelling: GARCH (1,1) estimated on annual global average goods export returns; model adequacy assessed via ACF of squared standardized residuals.  
-Time varying correlation: Rolling-5 year window used to compute volatility standardized trade and GDP shocks and their correlation.  
-Group comparisons: Countries classified by pre crisis export composition (>50% services meant service-dominant) and trade openness thresholds (<30%, 30–60%, 60-100%, 100-200%, >200%).  
-Atypicality detection: Residuals from pooled OLS regression of trade openness on GDP growth used to identify persistently deviant countries (mean absolute residual, ≥10 years of data).
 
## Key Results

-Post 2008 divergence: Trade volatility increased by 87.4%; GDP volatility declined by 21.4%.  
-Decoupling in normal times: Average trade-GDP correlation ≈ −0.06 (1990–2024), but recouples strongly during crises (e.g., ρ = −0.81 in 2009).  
-Service resilience: Service dominant economies experienced smaller GDP contractions during the GFC (-1.11% vs. -3.94%).  
-Openness threshold: Countries with trade openness <60% of GDP had significantly milder crisis impacts.  
-Persistent outliers: Top atypical countries (e.g., Singapore, Luxembourg, Djibouti) exhibit structural exceptionalism not generalizable to mainstream economies.  
-Volatility persistence: Goods export volatility shocks have a half-life of 9.1 years.  
-ICT role: ICT services contribute meaningfully to service export growth, with rising share over time.

## Repository Contents
notebooks/

├── 01_data_preparation.ipynb          # Variable construction, transformations
├── 02_stationarity_unit_root.ipynb    # ADF/KPSS tests
├── 03_structural_break_analysis.ipynb # Chow test, pre/post-GFC regressions
├── 04_garch_volatility.ipynb          # GARCH estimation, diagnostics
├── 05_rolling_dynamics.ipynb          # Volatility and correlation over time
├── 06_export_composition.ipynb        # Service vs. goods, ICT analysis
└── 07_resilience_thresholds.ipynb     # Openness bins, crisis impact by group

figures/      # All exported PNGs (300 DPI, white background)
tables/       # CSV outputs of key result tables
requirements.txt  # Exact package versions

## Reproduction Instructions

-Install dependencies:  
   pip install -r requirements.txt
-Place WDI data in a local directory and update file paths in trade_analysis.ipynb 
-Execute notebooks sequentially.  
-Figures and tables auto-save to /figures/ and /tables/.

## Dependencies
-pandas (1.5.3)
-numpy (1.24.3)  
-statsmodels (0.13.5)
-srch (5.3.0)
-linearmodels (4.27)  
-matplotlib (3.7.1)  
-seaborn (0.12.2)
(See requirements.txt for full list.)

## Author
Immaculate Nabaweesi
Contact: immaculatenabaweesi@gmail.com

