## Random Variables ##
Definition 2.1.1
	*A random variable is a function $X  : S \to \mathbb{R}$, where $S$ is a sample space.*

The distribution of $X$ is the probabilities that $X$ take a specific value as $s$ varies. That is, the collection of $P(X(s) = x)$ for each choice of $x$ as $s$ varies.

#### Indicator function ####
Let $A \subseteq S$. the indicator $I_A : S \to \{0,1\}$ such that 
$$
	I_A(s) = \begin{cases}
		1 \text{ if } s \in A \\
		0 \text{ otherwise.}
	\end{cases}
$$

Example: $S$  is the space of $5$ coin flips, $X(s)$ is the number of heads in $s\in S$ , then $P(X = 5) = \frac{1}{2^5}$.

## Distribution of Random Variable $X$ ##
definition 2.2.1
	_The distribution of a random variable $X$ is the collection of probabilities $P(X \in B)$ for all $B \subseteq \mathbb{R}$._
Strictly speaking, it is required for $B$ to be a Borel subset.

Note that $P(X\in B) = P(\{s: S \;|\; X(s) \in B\})$. 

The following statement are not very 'rigorous'/'formal' in mathematics, however, we allow it for our usage.

## Discrete Distribution ##
Definition 2.3.1
	_A random variable $X$ is __discrete__ if $\displaystyle \sum_{x \in \mathbb{R}} P(X = x) = 1$._
Definition 2.3.2
	*A random variable $X$ is discrete if there is a finite or countable sequence $\{x_i\}_{i = 0}^{K}$, $K \in \mathbb{N} \cup \{\infty\}$  of distinct real numbers such that $\displaystyle \sum_{i \in \mathbb{N}} P(X = x_i) = 1$.*
Definition 2.3.3
	The __probability function__ of a discrete random variable $X$ is the function $p_X : \mathbb{R} \to [0,1]$ such that $\displaystyle p_X(x) = P(X = x)$.

Theorem 2.3.1 (_Law of Total Probability for Discrete Random Variable_)
	Let $X$ be a discrete random variable, $A$ be some event. Then,
	$$ P(A) = \sum_{x\in\mathbb{R}} P(X = x) P(A | X = x)$$

#### Important Discrete Distributions####
Note: Every probability variable used below $\theta, \lambda$, etc. are in $[0,1]$.

_Degenerate distribution/Point (Mass) distribution_
	$p_c(c) = 1$ and $p_c(x) = 0$ for all $x \ne c$.
	
_Bernoulli($\theta$) distribution_
	Consider flipping a coin that has probability  of coming up heads and probability $\theta$ of coming up heads and $1−\theta$ of coming up tails, where $0 < \theta < 1$. Let $X = 1$ if the coin is heads, while $X = 0$ if the coin is tails. The probability distribution satisfies $p_X(1)  = P(X = 1) = \theta$ and $p_X(0) = P(X = 0) = 1 - \theta$. 
	The random variable $X$ is said to have the $\text{Bernoulli}(\theta)$ distribution, written as $X \thicksim \text{Bernoulli}(\theta)$. 

_Binomial($n, \theta$) distribution_
	Consider flipping $n$ coins each with independent probability $\theta$ of coming up heads and $1-\theta$ of coming up tails. Let $X$ be the number of heads showing, then$$
	p_X(x) = P(X = x) = \binom{n}{x} \theta^x(1-\theta)^{n-x} $$
	Where $x \in \mathbb{N}$ and $x\le n$. (Note we could define $\binom{n}{x} = 0$ whenever $x > n$ or $x < 0$). 
	The variable $X$ is said to have distribution $\text{Binomial}(n, \theta)$, written $X\thicksim\text{Binomial}(n, \theta)$. Notice $\text{Bernoulli}(\theta) = \text{Binomial}(1, \theta)$.
	Below is a plot of Binomial(20, 1/2) ($\bullet$) and Binomial(20, 1/5) ($\circ$).
		
	![[Pasted image 20231009184142.png]]
	An example of Binomial distribution:
	Consider $X_1,\ldots,X_n$ are independent random variables with a Bernoulli$(\theta)$ distribution. Then, $Y = X_1 + \ldots + X_n$ will have a Binomial$(n, \theta)$ distribution.

_Geometric$(\theta)$ distribution_
	Consider repeatedly flipping a coin that has probability $\theta$ of heads and $1-\theta$ of tails. Let $X$ be the number of tails that appear before the first head. Then $$p_X(k) = P(X = k) = \theta(1-\theta)^k$$
	![[Pasted image 20231009231108.png]]

_Negative-Binomial$(r, \theta)$ distribution_
	Consider repeatedly flipping a coin with probability $\theta$ of heads. Let $r\in\mathbb{N}^+$ and $Y$ be the number of tails that appear before the first $r$th head. Note that $Y = k \ge r$ happens only when $r-1$ heads has appeared in first $k + r -1$ flips and then heads at the $(r+k)$th flip, thus $$p_Y(k) = P(Y=k) = \binom{k + r - 1}{r-1}\theta^{r-1}(1-\theta)^{k}\theta = \binom{k + r - 1}{r-1}\theta^{r}(1-\theta)^{k} $$
	$Y$ is said to have the Negative-Binomial$(r, \theta)$ distribution, written $Y \thicksim \text{Negative-Binomial}(r, \theta)$. 
	![[Pasted image 20231009231906.png]]
	Note $\text{Geometric}(\theta) = \text{Negative-Binomial}(r, \theta)$. 

_Poisson$(\lambda)$ distribution_
	We say $Y \thicksim \text{Poisson}(\lambda)$ if $$p_Y(k) = P(Y = y) = \frac{\lambda^y}{y!} e^{-\lambda}$$
	![[Pasted image 20231009232350.png]]
	Motivation of the Poisson distribution:
	Consider $X \thicksim \text{Binomial}(n,\theta)$, setting $\theta = \frac{\lambda}{n}$, we have $$\begin{align*}P(X = x) &= \binom{n}{x} (\frac{\lambda}{n})^k(1-\frac{\lambda}{n})^{n-x} \\
	&=\frac{1}{x!} (1 - \frac{1}{n})\ldots(1 - \frac{x+1}{n})\lambda^x(1 - \frac{\lambda}{n})^n(1-\frac{\lambda}{n})^{-x}
	\end{align*}$$
	As $n\to\infty$, we have $(1-\frac{1}{n})\ldots(1-\frac{x+1}{n}) \to 1$ and $(1+\frac{-\lambda}{n})^n \to e^{-\lambda}$, thus $$P(X = x) = \frac{\lambda^x}{x!} e^{-\lambda}$$
	Practical interpretation:
	If it is known that the probability of event $A$ happening in an observation is $\theta$, then  the average number of events that occurs in the population of size $N$ is $\lambda = N\theta$. We can interpret the Poisson distribution as the distribution of the number of occurrence of event $A$ happening in a very large population ($N$ very large).
	Suppose Toronto has an average of $\lambda = 5$ fires a day. Then, the probability of $k$ fires happening is $$P(X = k) = \frac{\lambda^{k}}{k!} e^{-\lambda}$$
	![[Pasted image 20231010131754.png]]

_Hypergeometric$(N, M , n)$ distribution_
	Suppose that an urn contains $M$ white balls and $N − M$ black balls. Suppose we
	draw $n$ balls from the urn without replacement. 
	Note each collection has probability $\binom{N}{n}^{-1}$.
	Let $X$ be the number of red balls drawn.
	Observation:
		$X\ge0$, $X \le n$ and $X\le M$, so $0\le X\le \min\{n,M\}$. 
		At most $N - M$ can be blue, so $X \ge n - (N  - M)$.
		We want to find $P(X = k)$ such that $\max\{0, n - (N-M)\} \le k \le \min\{n, M\}$ which happens exactly when we got $k$ red and $n-k$ blue.
	The number of choices are $\binom{M}{k} \binom{N-M}{n-k}$. 
	Hence, $P(X=k) = \binom{M}{k} \binom{N-M}{n-k} / \binom{N}{n}$.

### Continuous Random Variable ###
$X$ is continuous if $P(X = x) = 0$ for all $x\in\mathbb{R}$.

_Uniform$[0,1]$ distribution_
	Consider a random variable $X : S \to [0,1]$, such that $$P(a \le x \le b) = b - a$$ where $0\le a\le b\le 1$ and $P(X < 0) = P(X > 1) = 0$. We say $X$ has a Uniform$[0,1]$ distribution, that is $X \thicksim \text{Uniform}[0,1]$.

Definition 2.4.2.
Let $f : \mathbb{R} \to \mathbb{R}$, then $f$ is a ___density function___ if $f(x) \ge 0$ for all $x\in\mathbb{R}$ and $\int_{-\infty}^{\infty} f(x) \:dx = 1$.

Definition 2.4.3
A random variable $X$ is _absolutely continuous_ if there is a density function $f$, such that $$P(a \le X \le b) = \int_{a}^{b} f(x) \: dx$$
