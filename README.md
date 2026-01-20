# SiyaKhosla_102303742_Assignment1
Learning Probability Density Function using a Roll-Number-Parameterised Non-Linear Model
Overview
This assignment focuses on understanding probability density functions (PDFs) by applying a non-linear transformation to real-world air quality data and then learning the parameters of a Gaussian-like probability density function. The implementation is carried out using Python in Google Colab, and the results are visualised and analysed.
Dataset Description
	Dataset: India Air Quality Data
	Source: Kaggle
	Feature Used: NO₂ (Nitrogen Dioxide concentration)
	The dataset contains air pollution measurements collected across various Indian cities over multiple years.
Only the NO₂ column is used in this assignment, and missing values are removed before further processing.
Methodology
	 Data Loading and Preprocessing
	The dataset is downloaded from Kaggle as a ZIP file and extracted in Google Colab.
	The CSV file is loaded using Pandas.
	The no2 column is selected as the input feature x.
	Missing values are removed to ensure clean numerical computation.
	Roll-Number-Parameterised Non-Linear Transformation
       Each value of xis transformed into a new variable zusing the following function:
z=x+a_r sin⁡(b_r x)
       Where:
        ris the university roll number
a_r=0.05×(r" " mod" " 7)
b_r=0.3×((r" " mod" " 5)+1)
      This transformation introduces controlled non-linearity into the data while preserving its 
      statistical structure.       
                       
	Learning the Probability Density Function
The transformed variable z is modelled using the following probability density function:
p ̂(z)=c⋅e^(-λ(z-μ)^2 )

Where:
μis the mean of z
λcontrols the spread of the distribution
cis the normalisation constant

Parameter Estimation:
	Mean (μ) is computed using the sample mean of z
	Variance (σ²) is computed using the sample variance
	Lambda (λ) is calculated as:
λ=1/(2σ^2 )

	Constant (c) is calculated as:
                                                                          c=√(λ/π)
Results
Learned Parameters
Parameter	Value
μ (Mean)	25.806857
λ (Lambda)	0.001460
c (Constant)	0.021557

These values define the learned probability density function for the transformed variable z.

Result Visualization
	A histogram of the transformed variable zis plotted to show the empirical distribution.
	The learned PDF is overlaid as a red curve on the histogram.
	This visualisation helps compare the real data distribution with the learned probabilistic model.
 

Observations and Insights
	The non-linear transformation slightly perturbs the original NO₂ values while preserving their overall distribution.
	The learned PDF captures the central tendency of the data effectively.
	Real-world pollution data shows long tails, which explains deviations between the histogram and the ideal Gaussian curve at extreme values.

Tools and Technologies Used
	Google Colab
	Python
	NumPy
	Pandas
	Matplotlib



