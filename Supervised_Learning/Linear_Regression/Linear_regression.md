---

<h1 align="center" style="color:white;">Linear Regression</h1>

---

## 🧠 1. Core Mathematical Concepts

* **Linear Algebra**: Vectors, matrices, dot product.
* **Statistics**: Mean, variance, covariance.
* **Optimization**: Minimizing a loss function using calculus.
* **Calculus**: Derivatives (for gradient descent).

---

## 🧮 2. Key Equations

### ✅ **Prediction Equation (Hypothesis Function)**:

$$
\hat{y} = w_0 + w_1x_1 + w_2x_2 + \dots + w_nx_n = \mathbf{w}^\top \mathbf{x}
$$

Or, for a single feature:

$$
\hat{y} = w_0 + w_1x
$$

### ✅ **Loss Function (Mean Squared Error)**:

$$
\text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (\hat{y}_i - y_i)^2
$$

### ✅ **Gradient Descent Update Rule**:

$$
w_j := w_j - \alpha \cdot \frac{\partial}{\partial w_j} \text{MSE}
$$

$$
\text{Where } \frac{\partial}{\partial w_j} \text{MSE} = \frac{2}{n} \sum_{i=1}^n (\hat{y}_i - y_i)x_{ij}
$$

---

## 🔍 3. Concept Breakdown (Step-by-Step)

### 💡 The Idea:

We want to fit a **straight line** (or a hyperplane in higher dimensions) to data that best predicts the output $y$ from input $x$.

---

### 📌 Step 1: Model Equation

We assume the relationship is linear:

$$
\hat{y} = w_0 + w_1x
$$

* $w_0$ is the **intercept** (bias).
* $w_1$ is the **slope** (weight).

---

### 📌 Step 2: Measure How Good the Line Is

We use **Mean Squared Error (MSE)** to measure how far off our predictions are:

$$
\text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (w_0 + w_1x_i - y_i)^2
$$

---

### 📌 Step 3: Minimize the Error

To find the **best** $w_0$ and $w_1$, we minimize the MSE using:

#### 👉 Gradient Descent:

We move the weights step-by-step in the **opposite direction** of the gradient.

$$
w_0 := w_0 - \alpha \cdot \frac{\partial}{\partial w_0} \text{MSE}
$$

$$
w_1 := w_1 - \alpha \cdot \frac{\partial}{\partial w_1} \text{MSE}
$$

Where:

$$
\frac{\partial}{\partial w_0} \text{MSE} = \frac{2}{n} \sum_{i=1}^n (\hat{y}_i - y_i)
$$

$$
\frac{\partial}{\partial w_1} \text{MSE} = \frac{2}{n} \sum_{i=1}^n (\hat{y}_i - y_i) x_i
$$

---

## 🧠 4. Numerical Example

Suppose we have this dataset with 3 points:

| x | y |
| - | - |
| 1 | 2 |
| 2 | 3 |
| 3 | 5 |

---

### Step-by-Step:

Let’s use **1 iteration of gradient descent**.

* Initial weights: $w_0 = 0$, $w_1 = 0$
* Learning rate: $\alpha = 0.01$

#### 🔹 Step 1: Predictions

$$
\hat{y}_1 = 0 + 0 \cdot 1 = 0 \\
\hat{y}_2 = 0 + 0 \cdot 2 = 0 \\
\hat{y}_3 = 0 + 0 \cdot 3 = 0
$$

#### 🔹 Step 2: Compute Gradients

$$
\frac{\partial}{\partial w_0} = \frac{2}{3} \left[(0 - 2) + (0 - 3) + (0 - 5)\right] = \frac{2}{3} \cdot (-10) = -6.67
$$

$$
\frac{\partial}{\partial w_1} = \frac{2}{3} \left[(0 - 2)(1) + (0 - 3)(2) + (0 - 5)(3)\right] \\
= \frac{2}{3} \cdot (-2 - 6 - 15) = \frac{2}{3} \cdot (-23) = -15.33
$$

#### 🔹 Step 3: Update Weights

$$
w_0 := 0 - 0.01 \cdot (-6.67) = 0.0667 \\
w_1 := 0 - 0.01 \cdot (-15.33) = 0.1533
$$

New model:

$$
\hat{y} = 0.0667 + 0.1533x
$$

---

## 🧠 Want a Practice Problem?

Here’s one you can solve:

### Problem:

Given the data:

| x | y |
| - | - |
| 1 | 1 |
| 2 | 2 |
| 3 | 2 |

Use one step of gradient descent to update $w_0 = 0$, $w_1 = 0$ with $\alpha = 0.1$
 😊

---

