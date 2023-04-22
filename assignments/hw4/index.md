# Homework4

## (1) Average Entropy

Let $H(p) = −p\log_2{p}-(1-p)\log_2{(1-p)}$ be the entropy function of a binary source. 

### (a) Use $\log_2 3 = 1.585$, to evaluate H(1/3).

$$
\begin{aligned}
H(1/3)
&=−\frac{1}{3}\log_2\frac{1}{3}−\frac{2}{3}\log_2\frac{2}{3}\\
&=-\frac{1}{3}\times1.585-\frac{2}{3}\times0.585=0.918
\end{aligned}
$$

### (b) Calculate the average entropy $H(p)$ when the probability $p$ is chosen uniformly in the range $0 ≤ p ≤ 1$.

$$
\begin{aligned}
\bar{H}(p)
&=\int_0^1H(p)dp\\
&=\int_0^1−p\log_2{p}-(1-p)\log_2{(1-p)}dp\\
&=\frac1{\ln2}\int_0^1−p\ln{p}dp+\int_0^1-(1-p)\ln{(1-p)}dp\\
&=\frac2{\ln2}\int_0^1−p\ln{p}dp\\
&=\frac1{2\ln2}
\end{aligned}
$$

## (2) Mutual Information for correlated normal distributions

$X$ and $Y$ are two correlated random normal variables with the following joint probability 

Evaluate $I(X; Y)$ and comment on the cases when $\rho = 1, 0$ and $-1$.

> For simplification, we use the this definition $I(X)=-\ln{p(X)}$, then $H(X)=E[I(X)]$ 

$$
\begin{aligned}
\begin{pmatrix}
X\\
Y
\end{pmatrix}
&\sim
N_2\left(0,
\begin{bmatrix}
\sigma^2&\rho\sigma^2\\
\rho\sigma^2&\sigma^2
\end{bmatrix}
\right)
\end{aligned}
$$

Evaluate $I(X; Y)$ and comment on the cases when $\rho = 1, 0$ and $-1$.

$$
\begin{aligned}
I(X; Y)
&=H(X)+H(Y)-H(X,Y)\\
\end{aligned}
$$

where

$$
\begin{aligned}
H(X)
&=E[-\ln p(X)]\\
&=E\left[-\ln\left(\frac{1}{\sqrt{2\pi\sigma^2}}\exp\left(-\frac{X^2}{2\sigma^2}\right)\right)\right]\\
&=E\left[\frac{X^2}{2\sigma^2}+\frac12\ln(2\pi\sigma^2)\right]\\
&=\frac1{2\sigma^2}E[X^2]+\frac12\ln(2\pi\sigma^2)\\
&=\frac12+\frac12\ln(2\pi\sigma^2)\\
\end{aligned}
$$

thus, $H(X)+H(Y)=1+\ln(2\pi\sigma^2)$

$$
p(x,y)=\frac{1}{2\pi\sigma^2\sqrt{1-\rho^2}}\exp\left(-\frac{x^2+y^2-2\rho xy}{2\sigma^2(1-\rho^2)}\right)
$$

$$
\begin{aligned}
H(X,Y)
&=E[-\ln p(X,Y)]\\
&=E\left[-\ln\left(\frac{1}{2\pi\sigma^2\sqrt{1-\rho^2}}\exp\left(-\frac{X^2+Y^2-2\rho XY}{2\sigma^2(1-\rho^2)}\right)\right)\right]\\
&=E\left[\frac{X^2+Y^2-2\rho XY}{2\sigma^2(1-\rho^2)}+\ln(2\pi\sigma^2\sqrt{1-\rho^2})\right]\\
&=\frac1{2\sigma^2(1-\rho^2)}E[X^2+Y^2-2\rho XY]+\ln(2\pi\sigma^2)+\frac12\ln(1-\rho^2)\\
&=1+\ln(2\pi\sigma^2)+\frac12\ln(1-\rho^2)\\
\end{aligned}
$$

thus 

$$
I(X;Y)=H(X)+H(Y)-H(X,Y)=-\frac12\ln(1-\rho^2)
$$

1. When $\rho=1$ or $-1$, $I(X;Y)=+\infty$. In this case, we can exactly know $Y$ given $X$, so the mutual information is maximized.
2. When $\rho=0$, $I(X;Y)=0$. In this case, $X$ and $Y$ are independent, so we can't know anything about $Y$ given $X$, so the mutual information is 0.

## (3) Channel Capacity

Consider a binary asymmetric communication channel, whose input source is the
alphabet X = {0, 1} with probabilities {0.5, 0.5}; whose output alphabet is Y = {0, 1};
and whose channel matrix is

$$
\begin{bmatrix}
1-\alpha&\beta\\
\alpha&1-\beta
\end{bmatrix}
$$

Where $\alpha$ is the probability of transmission error when sending $X=0$ and $\beta$ is the probability of transmission error when sending $X=1$.

### (a) What is the entropy of the source, $H(X)$?

$$
\begin{aligned}
H(X)
&=−p_0\log_2{p_0}−p_1\log_2{p_1}\\
&=−\frac12\log_2{\frac12}−\frac12\log_2{\frac12}\\
&=1
\end{aligned}
$$

### (b) What is the probability distribution of the outputs, p(Y), and the entropy of this output distribution, H(Y)?

$$
\begin{aligned}
P\begin{pmatrix}
Y=0\\
Y=1
\end{pmatrix}
&=\begin{pmatrix}
1-\alpha&\beta\\
\alpha&1-\beta
\end{pmatrix}
\begin{pmatrix}
\frac12\\
\frac12
\end{pmatrix}\\
&=\frac12\begin{pmatrix}
1-\alpha+\beta\\
\alpha+1-\beta
\end{pmatrix}
\end{aligned}
$$

$$
\begin{aligned}
H(Y)
&=-P(Y=0)\log_2{P(Y=0)}-P(Y=1)\log_2{P(Y=1)}\\
&=-\frac{1-\alpha+\beta}2\log_2{\frac{1-\alpha+\beta}2}-\frac{\alpha+1-\beta}2\log_2{\frac{\alpha+1-\beta}2}\\
&=1-\frac{1-\alpha+\beta}2\log_2\left(1-\alpha+\beta\right)-\frac{\alpha+1-\beta}2\log_2\left(\alpha+1-\beta\right)\\
\end{aligned}
$$

### (c) What is the joint probability distribution for the source and the output, p(X, Y), and what is the joint entropy, H(X, Y)?

$$
P(Y=i|X=j)=\begin{pmatrix}
1-\alpha&\beta\\
\alpha&1-\beta
\end{pmatrix}_{ij}
$$

$$
\begin{aligned}
P(X=j,Y=i)
&=P(Y=i|X=j)P(X=j)\\
&=\frac12\begin{pmatrix}
1-\alpha&\beta\\
\alpha&1-\beta
\end{pmatrix}_{ij}
\end{aligned}
$$

$$
\begin{aligned}
H(X,Y)
&=-\sum_{i=0}^1\sum_{j=0}^1P(X=j,Y=i)\log_2{P(X=j,Y=i)}\\
&=1-\frac{\alpha}2\log_2{\alpha}-\frac{\beta}2\log_2{\beta}-\frac{1-\alpha}2\log_2(1-\alpha)-\frac{1-\beta}2\log_2(1-\beta)\\
\end{aligned}
$$

### (d) What is the mutual information of this channel, $I(X; Y)$, as a function of $\alpha$ and $\beta$?

$$
\begin{aligned}
I(X;Y)
&=H(X)+H(Y)-H(X,Y)\\
&=1+1-\frac{1-\alpha+\beta}2\log_2\left(1-\alpha+\beta\right)-\frac{\alpha+1-\beta}2\log_2\left(\alpha+1-\beta\right)\\
&\quad -\left(1-\frac{\alpha}2\log_2{\alpha}-\frac{\beta}2\log_2{\beta}-\frac{1-\alpha}2\log_2(1-\alpha)-\frac{1-\beta}2\log_2(1-\beta)\right)\\
&=1-\frac{1-\alpha+\beta}2\log_2\left(1-\alpha+\beta\right)-\frac{\alpha+1-\beta}2\log_2\left(\alpha+1-\beta\right)\\
&\quad +\frac{\alpha}2\log_2{\alpha}+\frac{\beta}2\log_2{\beta}+\frac{1-\alpha}2\log_2(1-\alpha)+\frac{1-\beta}2\log_2(1-\beta)\\ 
\end{aligned}
$$

### (e) How many combinations of $(\alpha, \beta)$ are there for which the mutual information of this channel is maximal? What are those values, and what then is the capacity of such a channel in bits?

First of all, in order to find the extremum, we need to take gradient of $I(X;Y)$ with respect to $\alpha$ and $\beta$.

$$
\begin{cases}
\frac{\partial I(X;Y)}{\partial\alpha}=\frac{\ln(α)−\ln(1−α)+\ln(−α+β+1)−\ln(α−β+1)}{2\ln(2)}\\
\frac{\partial I(X;Y)}{\partial\beta}=\frac{\ln(β)−\ln(1−β)−\ln(−α+β+1)+\ln(α−β+1)}{2\ln(2)}
\end{cases}
$$

Then set the gradient to be zero and solve for $\alpha$ and $\beta$, get the solution of extremum set: 
$$
(\alpha, \beta) \in \{\alpha+\beta=1\}.
$$

After considering the extremum, we should consider the border of definition region of $(\alpha, \beta)$ by computing the value of $I(X;Y)$ at the border.

To illustrate the value of $I(X;Y)$, we plot the value of $I(X;Y)$ in the region $[0,1]\times[0,1]$. The plot is shown below.

![plot of I(X,Y)](img/I(X,Y).png)

From the analysis and the plot, we can see that the mutual information is maximal when $(\alpha, \beta) \in \{(0,0),(1,1)\}$. The capacity is $1$ bit.

### (f) What condition do $(\alpha, \beta)$ satisfy when the capacity of this channel is minimal? What is the channel capacity in that case?

From the analysis and the plot, ist's easy to see that when $\alpha+\beta=1$, the mutual information is minimal. The capacity is $0$ bit.

## (4) Principle of Maximum Entropy

### (a) Start with a given distribution for an “unfair” die with distribution {1/12, 1/12 , 1/6, 1/6, 1/4, 1/4}. Calculate the best guess of the distribution for the cases

#### (i) of no information

It's esay to see that the best guess is the uniform distribution $p_i=1/6$.

#### (ii) the case of knowing only the average  $\sum_{i=1}^6ip_i=\frac{25}6$ .

Form the Lagrangian function:

$$
\begin{aligned}
L(p;\lambda_0,\lambda_1)=-\sum_{i=1}^6p_i\ln{p_i}
+\lambda_0\left(\sum_{i=1}^6p_i-1\right)+\lambda_1\left(\sum_{i=1}^6p_i-\frac{25}6\right)
\end{aligned}
$$

Take the derivative with respect to $p_i$:

$$
\begin{aligned}
\frac{\partial L}{\partial p_i}
&=-1-\ln{p_i}+\lambda_0+i\lambda_1\\
\end{aligned}
$$

Set it to zero, then get:

$$
\begin{aligned}
p_i&=\exp(-1+\lambda_0+\lambda_1i)=\frac{e^{\lambda_1i}}{\sum e^{\lambda_1i}}\\
\end{aligned}
$$

Then solve the $\lambda_0,\lambda_1$ by the constraint:

$$
\begin{aligned}
\sum_{i=1}^6p_i&=\exp(-1+\lambda_0)\sum ie^{\lambda_1i}=1\\
\sum_{i=1}^6ip_i&=\frac{\sum ie^{\lambda_1i}}{\sum e^{\lambda_1i}}=\frac{25}6\\
\end{aligned}
$$

Let $a=e^{\lambda_1}$, then we get:

$$
\begin{aligned}
6\sum_{i=1}^6ia^i&=25\sum_{i=1}^6a^i\\
\sum_{i=1}^6 (6i-25)a^i&=0\\
11 a^6 + 5 a^5 - a^4 - 7 a^3 - 13 a^2 - 19 a &= 0\\
a&\approx 1.26661
\end{aligned}
$$

Then the $\lambda_1=\ln1.26661\approx0.239$.

Then the distribution is:

$$
\begin{aligned}
p_i&=\frac{e^{\lambda_1i}}{\sum e^{\lambda_1i}}\\
&=\frac{e^{0.239i}}{\sum e^{0.239i}}\\
\end{aligned}
$$

### (b) Let $p_i$ by the probabilities of a particle having energy level $\epsilon_i$, respectively, where $n$ is the number of energy levels, and let the mean value of energy be $\bar\epsilon$. By maximizing the Shannon entropy,

$$
\begin{aligned}
H(p)=-\sum_{i=1}^np_i\ln{p_i}
\end{aligned}
$$

Subject to,

$$
\begin{cases}
\sum_{i=1}^np_i&=1\\
\sum_{i=1}^n\epsilon_ip_i&=\bar\epsilon\\
\end{cases}
$$

Form the Lagrangian function:

$$
\begin{aligned}
L(p;\lambda_0,\lambda_1)=-\sum_{i=1}^np_i\ln{p_i}
+\lambda_0\left(\sum_{i=1}^np_i-1\right)+\lambda_1\left(\sum_{i=1}^n\epsilon_ip_i-\bar\epsilon\right)
\end{aligned}
$$

Take the derivative with respect to $p_i$:

$$
\begin{aligned}
\frac{\partial L}{\partial p_i}
&=-1-\ln{p_i}+\lambda_0+\epsilon_i\lambda_1\\
\end{aligned}
$$

Set it to zero, then get:

$$
\begin{aligned}
p_i&=\exp(-1+\lambda_0+\epsilon_i\lambda_1)=\frac{e^{\epsilon_i\lambda_1}}{\sum e^{\epsilon_i\lambda_1}}\\
\end{aligned}
$$

> Since I am not a student in physics major, so I just follow the hint that "identify one of the Lagrange multiplier $\lambda_1$ to be equal to $-1/kT$".

Then get the distribution:

$$
\begin{aligned}
p_i&=\frac{e^{-\epsilon_i/kT}}{\sum e^{-\epsilon_i/kT}}\\
\end{aligned}
$$

Then, it's easy to get the mean value of energy:

$$
\begin{aligned}
\bar\epsilon&=\sum_{i=1}^n\epsilon_ip_i\\
&=\sum_{i=1}^n\epsilon_i\frac{e^{-\epsilon_i/kT}}{\sum e^{-\epsilon_i/kT}}\\
&=\frac{\sum_{i=1}^n\epsilon_ie^{-\epsilon_i/kT}}{\sum_{i=1}^n e^{-\epsilon_i/kT}}\\
\end{aligned}
$$
