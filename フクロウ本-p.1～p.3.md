<div style="text-align: center;">
    <img src="フクロウ本表紙.png" width="200">
</div>

#### 1.1.1 Density function, expectation, variance

A real-valued random variable $X$ is often described by means of its cumulative distribution function $CDF$,

$$
F_X(x) := \mathbb{P}[X \le x],
$$


$$
f_X(x) := \frac{dF_X(x)}{dx}.
$$

Let $X$ be a continuous real-valued random variable with $PDF$ $f_X(x)$. The expected value of $X$,  $\mathbb{E}[X]$ , is defined as

$$
\mathbb{E}[X] = \int_{-\infty}^{+\infty} x f_X(x) \, dx
= \int_{-\infty}^{+\infty} x \frac{dF_X(x)}{dx} \, dx
= \int_{-\infty}^{+\infty} x \, dF_X(x),
$$

provided the integral  $\int_{-\infty}^{+\infty} |x| f_X(x)\, dx$  is finite.

The variance of $X$,  $\mathrm{Var}[X]$ , is defined as

$$
\mathrm{Var}[X] = \int_{-\infty}^{+\infty} (x - \mathbb{E}[X])^2 f_X(x)\, dx,
$$

provided the integral exists.

For a continuous random variable $X$ and some constant $a \in \mathbb{R}$, the expectation of an indicator function is related to the $CDF$ of $X$ as follows:

$$
\mathbb{E}[1_{X \le a}]
= \int_{\mathbb{R}} 1_{x \le a} f_X(x)\, dx
= \int_{-\infty}^{a} f_X(x)\, dx
=: F_X(a),
$$

where $F_X(\cdot)$ is the $CDF$ of $X$, and $1_{X \in \Omega}$ is the indicator function of the set $\Omega$. The indicator function is defined as

$$
1_{X \in \Omega} =
\begin{cases}
1, & X \in \Omega, \\
0, & X \notin \Omega .
\end{cases}
\tag{1.1}
$$

<!-- ##### Definition 1.1.1 (Survival probability)
The survival probability is directly linked to the $CDF$. If $X$ is a random variable which denotes the lifetime, for example, in a population, then $\mathbb{P}[X \le x]$ indicates the probability of not reaching the age $x$. The survival probability, defined by

$$
\mathbb{P}[X > x] = 1 - \mathbb{P}[X \le x] = 1 - F_X(x),
$$

then indicates the probability of surviving a lifetime of length $x$. -->

---

##### Normal distribution

A basic and well-known example of a random variable is the normally distributed random variable.
A normally distributed stochastic variable $X$, with expectation $\mu$ and variance $\sigma^2$, is governed by the following probability distribution function:

$$
F_{N(\mu, \sigma^2)}(x)
= \mathbb{P}[X \le x]
= \frac{1}{\sigma \sqrt{2\pi}}
\int_{-\infty}^{x}
\exp\left( -\frac{(z - \mu)^2}{2\sigma^2} \right)
dz.
\tag{1.2}
$$

Variable $X$ then is said to have an $N(\mu, \sigma^2)$-normal distribution. The corresponding probability density function reads:

$$
f_{N(\mu, \sigma^2)}(x)
= \frac{d}{dx} F_{N(\mu, \sigma^2)}(x)
= \frac{1}{\sigma \sqrt{2\pi}}
\exp!\left( -\frac{(x - \mu)^2}{2\sigma^2} \right).
\tag{1.3}
$$

---

##### Example 1.1.1 (Expectation, normally distributed random variable)

Let us consider $ X \sim N(\mu, 1) $. By the definition of the expectation, we find:

$$
\mathbb{E}[X]
= \int_{\mathbb{R}} x f_X(x)\, dx
= \frac{1}{\sqrt{2\pi}}
\int_{\mathbb{R}}
x \exp\!\left( -\frac{(x - \mu)^2}{2} \right) dx.
$$

We use the substitution $ z = x - \mu$. Then:

$$
\mathbb{E}[X]
= \frac{1}{\sqrt{2\pi}}
\int_{\mathbb{R}}
(z + \mu)\, \exp\!\left( -\frac{z^2}{2} \right) dz
$$

$$
= \frac{1}{\sqrt{2\pi}}
\int_{\mathbb{R}}
z \exp\!\left( -\frac{z^2}{2} \right) dz
\;+\;
\frac{\mu}{\sqrt{2\pi}}
\int_{\mathbb{R}}
\exp\!\left( -\frac{z^2}{2} \right) dz.
$$

The first integral is zero because $z e^{-z^2/2}$ is an odd function over symmetric limits. The second integral equals $\sqrt{2\pi}$. Thus,

$$
\mathbb{E}[X] = \mu.
$$

---

#### 1.1.2 Characteristic function

In computational finance, we typically work with the density function of certain stochastic variables, like for stock prices or interest rates, as it forms the basis for computation of expectations or variances. For some basic stochastic variables the density is known in closed form, but for relevant stochastic processes in finance we often do not know the density.

The **characteristic function (ChF)**, $\varphi_X(u)$ for $u \in \mathbb{R}$, of the random variable (X), is the Fourier–Stieltjes transform of the cumulative distribution function $F_X(x)$, i.e., with (i) the imaginary unit,

$$
\varphi_X(u)
:= \mathbb{E}[e^{iuX}]
= \int_{-\infty}^{+\infty} e^{iux}, dF_X(x)
= \int_{-\infty}^{+\infty} e^{iux}, f_X(x), dx.
\tag{1.4}
$$

...