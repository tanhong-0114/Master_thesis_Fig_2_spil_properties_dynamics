## 📖 Master's Thesis
My full master's thesis, titled **"The associations between soil properties and aphid abundance in soybean agroecosystem"**, is officially published and available for download here:
* [NTU Theses and Dissertations Repository (臺灣大學碩博士論文典藏系統)](http://tdr.lib.ntu.edu.tw/jspui/handle/123456789/101430)
*Permanent DOI*: [https://doi.org/10.6342/NTU202600178](https://doi.org/10.6342/NTU202600178)

# 📊 Soybean Agroecosystem Microclimate Analysis (圖二)

This repository contains the R programming workflow and automated data visualization pipeline used to analyze and plot microclimate dynamics (Soil Temperature, Soil Moisture, and Soil Electrical Conductivity) within the soybean agroecosystem for **Chapter 3 (Results) / Fig. 2** of my Master's Thesis.
My Master's Thesis only showed the results of soil moisture and soil electrical conductivity.

---

## 📌 Data Pipeline & Visualization Overview

The script (`figure 1.R`) executes a comprehensive workflow from raw IoT microclimate data to publication-ready multipanel figures, integrating **parametric statistics (ANOVA)**, **multiple comparisons (EMMeans)**, and **dual-axis correlation workflows**.

### 🔹 Figure 1: Spatiotemporal Dynamics & Seasonal Comparisons
* **Panels A, B, C (Time-Series Dynamic Plots):**
  * Tracks `Daily Mean Soil Temperature`, `Soil Moisture (%)`, and `Soil Electrical Conductivity (dS/m)` over time for both **2024 Spring** and **2024 Fall** seasons.
  * Uses `stat_summary(fun.data = "mean_cl_normal")` to automatically compute and render **95% Confidence Interval (CI) ribbons** around the mean trajectory line.
  * Includes transparent multi-line mapping for individual experimental field blocks (`block`) to display intra-seasonal spatial variances under an aggregated bold average trend.
* **Panels D, E, F (Statistical Boxplots):**
  * Conducts 2-sample parametric comparisons between Spring and Fall seasons.
  * Integrates a linear model (`lm`) post-hoc framework with `emmeans` and `multcomp::cld` to automatically generate compact letter displays (`Letters=letters`) representing statistical significance levels.

### 🔹 Figure 2: Soil Moisture & EC Dual-Axis Interaction & Correlation
* **Dual-Axis Integration:** Features advanced `ggplot2::sec_axis` scaling transformations to superimpose `Soil Moisture` (Solid Line) and `Soil EC` (Dashed Line) on a single timeline, visually exploring covariate trends.
* **Correlation Modeling:** Computes Pearson's correlation tests (`cor.test`) for spring and fall datasets independently, rendering automated scatter plots with linear trendlines (`geom_smooth(method = "lm")`) along with dynamically annotated *p*-values and correlation coefficients (*r*).

---

## 🛠️ Required R Packages

Ensure you have the following libraries installed before running the script:

```r
# Key Visualization & Layout Packages
library(ggplot2)       # Elegant data visualization
library(tidyverse)     # Data manipulation (dplyr, tidyr)
library(ggpubr)        # Advanced plot arrangement (ggarrange)
library(cowplot)       # Streamlined subplot grids (plot_grid)
library(scales)        # Axis transformations

# Statistical & Post-Hoc Modeling Packages
library(car)           # Type-II ANOVA analyses
library(emmeans)       # Estimated marginal means
library(multcomp)      # Post-hoc multiple comparisons
library(multcompView)  # Compact letter display conversion
library(rcompanion)    # Normality histograms & distribution checks
