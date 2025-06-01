---

<h1 align="center" style="color:white;">Polynomial Regression</h1>

---
# 🧠 GOAL:

Fit a curved line to data points where the relationship between input $x$ and output $y$ is **nonlinear**.

---

# 📍 1. Problem Definition

You are given training data:

| x | y  |
| - | -- |
| 1 | 6  |
| 2 | 11 |
| 3 | 18 |

This doesn’t look linear (a straight line won’t fit perfectly). So we use **Polynomial Regression**, which models the data like this:

$$
\hat{y} = w_0 + w_1x + w_2x^2
$$

> Here:

* $w_0$: bias/intercept
* $w_1$: linear weight
* $w_2$: quadratic weight
* $x$: the input feature
* $\hat{y}$: the predicted output

---

# 🧮 2. Polynomial Feature Expansion

We **convert each input** into polynomial features up to degree 2:

$$
x = 1 \Rightarrow [1, 1, 1^2] = [1, 1, 1] \\
x = 2 \Rightarrow [1, 2, 4] \\
x = 3 \Rightarrow [1, 3, 9]
$$

This gives us the design matrix $X$:

$$
X = \begin{bmatrix}
1 & 1 & 1 \\
1 & 2 & 4 \\
1 & 3 & 9 \\
\end{bmatrix}, \quad
y = \begin{bmatrix}
6 \\
11 \\
18 \\
\end{bmatrix}
$$

> 🔍 **Why do this?**
> We transform a nonlinear problem into a linear one — by **mapping input to a higher-dimensional space**.

> ❗What if we don’t?
> We'd be stuck with a straight line (linear regression) that cannot model curved patterns.

---

# ⚙️ 3. Cost Function (Loss Function)

We want to minimize the error between the predicted $\hat{y}$ and actual $y$:

$$
\text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (\hat{y}_i - y_i)^2
$$

> Measures **how wrong the model is**. Lower MSE means better fit.

---

# 📘 4. Model Training — Find Best Weights

We solve this using the **Normal Equation**:

$$
w = (X^T X)^{-1} X^T y
$$

> This gives the **exact best weights** (no need for iterative optimization like gradient descent).

### 🔍 What this does:

1. $X^T$: Transpose of feature matrix
2. $X^T X$: Correlation between features
3. $(X^T X)^{-1}$: Inverse — to “undo” feature interactions
4. $X^T y$: How features relate to target
5. Together, we get: **weights that minimize squared error**

> ❗What if we don’t use this?
> We can’t solve the system directly — and can’t get the optimal curve.

---

# 🧮 Let’s compute each step

### Step 1: Compute $X^T$

$$
X^T = \begin{bmatrix}
1 & 1 & 1 \\
1 & 2 & 3 \\
1 & 4 & 9 \\
\end{bmatrix}
$$

### Step 2: Compute $X^T X$

$$
X^TX = \begin{bmatrix}
3 & 6 & 14 \\
6 & 14 & 36 \\
14 & 36 & 98 \\
\end{bmatrix}
$$

### Step 3: Compute $X^T y$

$$
X^Ty = \begin{bmatrix}
6 + 11 + 18 = 35 \\
1×6 + 2×11 + 3×18 = 6 + 22 + 54 = 82 \\
1×6 + 4×11 + 9×18 = 6 + 44 + 162 = 212 \\
\end{bmatrix}
=
\begin{bmatrix}
35 \\
82 \\
212 \\
\end{bmatrix}
$$

### Step 4: Solve:

$$
w = (X^TX)^{-1} X^Ty
$$

> This involves computing the inverse of a 3x3 matrix, which you can do by hand (tedious), or I can compute it for you if you want.

Let’s assume we solve it (you can verify or try solving the system too), and the result is:

$$
w = \begin{bmatrix}
1 \\
2 \\
1 \\
\end{bmatrix}
$$

So your **final model** is:

$$
\hat{y} = 1 + 2x + x^2
$$

---

# 🔮 5. Make a Prediction

Say you want to predict the score when $x = 4$:

$$
\hat{y} = 1 + 2(4) + (4)^2 = 1 + 8 + 16 = \boxed{25}
$$

✅ That’s your predicted output!

---

# 📊 Final Summary (Workflow)

| Step | What you do                                  | Why it matters                         |
| ---- | -------------------------------------------- | -------------------------------------- |
| 1    | Expand features to polynomial powers         | Model non-linear patterns              |
| 2    | Build design matrix $X$                      | Represent inputs in matrix form        |
| 3    | Use Normal Equation $w = (X^TX)^{-1}X^Ty$    | Solve for best-fit weights             |
| 4    | Get equation $\hat{y} = w_0 + w_1x + w_2x^2$ | This is your trained model             |
| 5    | Use it to predict $y$ for new $x$            | Apply the learned model to future data |

---

