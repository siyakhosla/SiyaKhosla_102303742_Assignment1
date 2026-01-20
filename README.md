# Learning Probability Density Function using a Roll-Number-Parameterised Non-Linear Model

## Overview
This project focuses on understanding **Probability Density Functions (PDFs)** by applying a roll-number-parameterised non-linear transformation to real-world air quality data and learning the parameters of a Gaussian-like PDF.

The implementation is carried out using **Python in Google Colab**, and the results are visualised and analysed.

---

## Dataset
- **Dataset:** India Air Quality Data  
- **Source:** Kaggle  
- **Feature Used:** NO₂ (Nitrogen Dioxide concentration)

Only the **no₂** column is used, and missing values are removed before further processing.

---

## Methodology

### 1. Data Loading and Preprocessing
- Dataset is downloaded from Kaggle and extracted in Google Colab  
- CSV file is loaded using **Pandas**  
- The **NO2** column is selected as input feature x.
- Missing values are removed to ensure clean numerical computation

---

### 2. Roll-Number-Parameterised Non-Linear Transformation
Each value of x is transformed into z using a roll-number-dependent non-linear function:

$$z = x + a_r \sin(b_r x)$$
Where r is the university roll number and the parameters $$a_r$$ and $$b_r$$ are defined as:

$$a_r = 0.05 \times (r \bmod 7)$$

$$b_r = 0.3 \times ((r \bmod 5) + 1)$$

This transformation introduces controlled non-linearity while preserving the statistical structure of the data.

---

### 3. Learning the Probability Density Function
The transformed variable is modelled using a Gaussian-like probability density function.

**Parameter Estimation:**
- Mean (μ) → Sample mean  
- Variance (σ²) → Sample variance  
- Lambda (λ) → Computed from variance.

$$\lambda = \frac{1}{2\sigma^2}$$
- Normalisation constant (c) → Computed analytically

$$c = \sqrt{\frac{\lambda}{\pi}}$$


---

## Results

### Learned Parameters

| Parameter | Value |
|---------|-------|
| μ (Mean) | 25.806857 |
| λ (Lambda) | 0.001460 |
| c (Constant) | 0.021557 |

---

## Result Visualization

- A histogram of the transformed variable is plotted to show the empirical distribution.  
- The learned PDF is overlaid as a red curve on the histogram.
- This visualisation helps compare the real data distribution with the learned probabilistic model.
 
<p align="center">
	<img width="610" height="433" alt="image" src="https://github.com/user-attachments/assets/c1c72025-38b1-4dd6-a5cc-b6a5d95d0153" />
</p>

---

## Observations and Insights
- The non-linear transformation slightly perturbs the original NO₂ values while preserving their overall distribution  
- The learned PDF captures the central tendency of the data effectively  
- Real-world pollution data exhibits long tails, explaining deviations at extreme values  

---

## Tools and Technologies Used
- Google Colab  
- Python  
- NumPy  
- Pandas  
- Matplotlib  
