Bertram Nicolai Hage - s224918

## Problem 1

#### Question 1.1
The decision maker in in the decision-maker problem is the friend and the decisions that can be made is one of the three dates described, A, B, or C.

The exegenous variables in this case is the quality of the date which in the problem is assumed to be binary, i.e. the date either turns out good or bad. While it could be argued the decision-maker might have an effect of the date turning out well it is not assumed to be the case here.

#### Question 1.2
In the below table is the payoff table for the system, displaying the utility for all potential combinations of decisions and states of nature.

|        | Date goes well | Date goes bad |
| ------ | -------------- | ------------- |
| Date A | 80             | 60            |
| Date B | 100            | 10            |
| Date C | 70             | 65            |

#### Question 1.3
By using the $Maximax$ strategy we will choose the decision that yields the highest utility overall, regardless of the state of nature.

We choose $M_{i}=\max(O_{i, good}, O_{i, bad})$, for $i=A, B, C$.

Looking at the payoff table from 1.2 this will be option B.

Using the $Maximin$ strategy we seek to choose the decision that yields the highest utility, given the worst case scenario for the state of nature, in our case this is if the date goes bad.

We choose $M_i=max(O_{i, bad})$ for $i=A,B,C$.

Looking at the payoff table from 1.2 this will be option C.

#### Question 1.4
Deducing the regret table we need to, for each scenario of states of nature, calculate the for each decision the regret, meaning the utility we missed out on by not choosing the optimal for that state of nature.

We get the following regret table

|        | Date goes well | Date goes bad |
| ------ | -------------- | ------------- |
| Date A | 20             | 5             |
| Date B | 0              | 55            |
| Date C | 30             | 0             |
By following the $Minimax$ strategy we choose the decision that has the lowest maximum regret, which in this case is option A.

#### Question 1.5
The expected utility maximization EUM can be calculated by
$$
\max_x \mathbb{E}_\omega [C(x,\omega)]
$$
For a given value $p$ the EUM for each option is
$A: 80\cdot p + 60\cdot(1-p)$
$B: 100\cdot p + 10\cdot(1-p)$
$C:70\cdot p+65\cdot(1-p)$

Op the following plot $p$ is plotted along the horizontal axis and the EUM is plotted along the vertical axis. A is the blue line, B is the green line and C is the purple line.
```desmos-graph
left=-0.1; right=1; bottom=-0.1; top=100;
grid=false;
---
80*x+60*(1-x)
100*x+10*(1-x)
70*x+65*(1-x)
```

For the case of $p=0.6$ the EUM is
$A: 80\cdot 0.6 + 60\cdot(1-0.6)=72$
$B: 100\cdot 0.6 + 10\cdot(1-0.6)=64$
$C:70\cdot 0.6+65\cdot(1-0.6)=68$.

Thus option A is to prefer. Generally speaking, looking at the graph it can be seen that option C is to prefer when $p< \frac{1}{3}$, option A is to prefer when $\frac{1}{3}<p< \frac{5}{7}$, and option B is to prefer when $p> \frac{5}{7}$.

Thus, I would select the same strategy as the $Maximax$ strategy when $p> \frac{5}{7}$.

## Problem 2
#### Question 2.1
This is a discrete Markov chain.

A state is denoted by what is left of cups at the end of the day. Let the state at time $t$ be denoted by $X_{t}$. We define the time steps between a given $t$ and $t+1$ as a day. We cannot have a state in the middel of the day. Thus $t\in 0\cap \mathbb{N}$ meaning tha the Markov chain is discrete.

#### Question 2.2
If 0 cups are left at the end of the day:
	3 cups will be delivered the next day. Thus a net demand of -3 will result in the state of 0 again.
	A demand of more than 3 will result in extra cups being sent back, thus, a net demand above 0 the next day wil result in a state of 3.
If 1 cups are left at the end of the day:
	No extra cups will be delivered. A net demand below -1 will mean there will be no cups left. Thus a net demand of -1 or below will result in a state 0. A net demand above 2 will result in extra cups being sent back, thus, if the net demand is 2 or more it will result in a state 3.
The same logic follows for state 2 and 3

The 1-step transition matrix is presented below.

| $X_t /X_{t+1}$ | 0    | 1    | 2    | 3    |
| -------------- | ---- | ---- | ---- | ---- |
| **0**          | 0.05 | 0.05 | 0.1  | 0.8  |
| **1**          | 0.2  | 0.35 | 0.2  | 0.25 |
| **2**          | 0.1  | 0.1  | 0.35 | 0.45 |
| **3**          | 0.05 | 0.05 | 0.1  | 0.8  |

#### Question 2.3
Defining the 1-step probability matrix $P$ we can calculate the steady state probabilities $\pi$ as
$$A=P^\top-I$$
$$A^*=\begin{bmatrix}&-A-&& \\
1 & 1 & 1 & 1
\end{bmatrix}$$
$$
b=\begin{bmatrix}0 & 0 & 0 & 0 & 1\end{bmatrix}
$$
$$
\pi=\frac{A^*}{b^\top} \approx 
\begin{bmatrix}
0.069 \\
0.082 \\
0.144 \\
0.705
\end{bmatrix}
$$
#### Question 2.4
If the cups reach 0 inventory, three new will be supplied the next day. If the cup inventory is 3 at the end of the day, it will be enough to meet any possible demand the next day. Thus, only in the case of the inventory ending as 1 or 2 will there be a risk of shortage.

The expected cost is thus
$$
\sum_{j=1}^{4} \pi_j\mathbb{E}[C(j)]=\pi_1(0.05+0.05)\cdot -30+\pi_2\cdot 0.05\cdot -30\approx 0.584   \, 
$$

## Problem 3
#### Question 3.1
Based on the information given we have 
$\mu = \frac{1}{2}$
$L_q=5.59$
$W = 8.4$

Using Little's formula we get:
$W = W_q+\frac{1}{\mu} \Leftrightarrow 8.4=W_q+2 \implies W_q = 6.4$
$L_q=\lambda W_q\Leftrightarrow 5.59=\lambda 6.4\implies \lambda=\frac{5.59}{6.4}\approx 0.873$
$L=\lambda W = 0.0873\cdot8.4 \approx 7.34$

## Problem 5
#### Question 5.1
The overage penalty is the penalty associated with ordering too many TV's. Thus the overage penalty is 1200-1000 DKK = 200. I denote the overage penalty $\pi_0=200$.

The underage penalty is the penalty associated with ordering too few TV's. Thus the underage penalty is 3000-1200 DKK. I denote the underage penalty $\pi_u=1800$.

The uncertainty parameter is the quarterly demand of TV's. I denote this $\omega$. $\omega$ is normally distributed with mean 30 and standard deviation of 10. We denote the distribution of $\omega$ as $f(\omega)$.

#### Question 5.2
We want to solve an expected utility maximization problem
$$
\min_x \mathbb{E}(\pi_u(\omega-x)_++\pi_o(x-\omega)_+)),
$$
where $x$ is the number of TV's ordered.

The optimal solution $x^*$ is calculated by
$$
x^* = F^{-1}\left( \frac{\pi_u}{\pi_u+\pi_o} \right)
$$
This yields the answer of approximately
$$
x^*\approx42.82.
$$
As there can only be ordered a whole amount the TV-vendor should order 43 TV's.

#### Question 5.3
Se papir

## Problem 6
#### Question 6.1

We rewrite the problem as
$$
\begin{align}
\min_{x,y,z} &&cx+qy \\
s.t. &&P[hx+y≥D]≥0.95 \\
&&y≥hz \\
&&x,y,z\in\mathbb{Z}_+
\end{align}
$$
where $P[hx+y≥D]≥0.95$ denotes that the probability that the demand constains hold must be at least 95%. Here $D\sim \mathcal{N}(2400, 300^2)$.

<!-- Manger deterministic equivalent -->

#### Question 6.2
The here and now decision is the amount of full time employees to hire, $x$.
The recourse decision is the amount of part time  hours to hire, $y$.
The stochastic parameter is the demand $D$.

#### Question 6.3
$$
\begin{align}
\min_{x,y,z} &&cx+\mathbb{E}_D[\min_y] \\
s.t. &&P[hx+y≥D]≥0.95 \\
&&y≥hz \\
&&x,y,z\in\mathbb{Z}_+
\end{align}
$$
