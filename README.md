# Probability Density Function Estimation (Assignment-1)

## Project Overview
This project performs statistical modeling on Air Quality Data ($NO_2$ levels) to estimate probability density functions (PDF). The workflow involves a roll-number-based data transformation followed by non-linear curve fitting to a Gaussian model.

**Dataset Used:** [India Air Quality Data (Kaggle)](https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data)

## Student Details
* **Roll Number:** 102317208
* **Assignment:** 1
* **Subject:** Machine Learning

## Mathematical Formulation

### 1. Data Transformation
The raw input feature $x$ ($NO_2$) is transformed into a new variable $z$ using the unique parameters derived from the University Roll Number ($r$).

$$z = x + a_r \sin(b_r x)$$

**Parameter Calculation:**
* **$a_r$**: $0.05 \times (r \pmod 7) = 0.05 \times 0 = \textbf{0}$
* **$b_r$**: $0.3 \times ((r \pmod 5) + 1) = 0.3 \times 4 = \textbf{1.2}$

Since $a_r = 0$, the transformation simplifies to an identity function:
$$\textbf{z = x}$$

### 2. Parametric Estimation
The transformed data ($z$) is fitted to the following probability density function model:

$$\hat{p}(z) = c \cdot e^{-\lambda(z - \mu)^2}$$

The objective is to find the optimal values for:
* **$c$** (Scale/Height)
* **$\lambda$** (Shape parameter)
* **$\mu$** (Mean/Location)

## Implementation Details
The solution is implemented in Python using `scipy.optimize.curve_fit` to minimize the least squares error between the data histogram and the theoretical model.

### Dependencies
* `numpy`: For numerical operations and histogram calculation.
* `pandas`: For data loading and preprocessing.
* `scipy`: For the curve fitting algorithm.
* `matplotlib`: For visualizing the fitted curve against the real data.

### How to Run
1.  Place the `city_day.csv` file in the same directory.
2.  Run the script:
    ```bash
    python assignment1.py
    ```
3.  The script will output the calculated values for $c$, $\lambda$, and $\mu$ and generate a plot comparing the model to the actual data distribution.

## Results
The calculated parameters obtained from the fitting process are submitted via the official assignment form.
