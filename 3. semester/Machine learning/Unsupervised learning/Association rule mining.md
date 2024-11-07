---
Uge: Uge 12 - 28/11/23
Pensum: Kap. 21
---
### Definition
Given a set of records each containing a number of items from a set.
**Goal**: Produce dependency rules. Meaning: predict the occurrence of an item based on occurrences of other items.

###### Example
![[Skærmbillede 2023-12-02 kl. 21.12.14.png]]
## Association analysis

>[!info] Terms
>**Item set**
>For example {Bread, Soda, Milk}, {Milk, Diaper}, { }
>
>**Support for an item set $\mathbf{X}$**
>Percentage of transactions that contain $X$
>
>**Association rule**
>Expression of the form $X\to Y$, where $X$ and $Y$ are disjoint item sets

>[!info] Support
>Support for a set $X$ over a number of transactions $T$
>$$
>supp(X)=\frac{\{\text{\# transactions containing }X\}}{N}
>=\frac{|\{t\in T|X\subseteq t\}|}{N}.
>$$
>**Support for an association rule $X\to Y$**
>Percentage of transactions that contain $X\cup Y$
>$$
>supp(X\to Y)= supp(X\cup Y)=\frac{|\{t\in T|X\cup Y\subseteq t\}|}{N}.
>$$

>[!info] Confidence
>Confidence for an association rule $X\to Y$ is the percentage of transactions containing $X$ that also contain $Y$
>$$
>conf(X\to Y)= \frac{supp(X\cup Y)}{supp(X)}
>$$

### Minima
Set a level $minsupp$ and $minconf$.
Find all association rules that have
- $\mathbf{Support}≥minsupp$
- $\mathbf{Confidence}≥minconf$

Approach:
- Frequent item set generation: Generate a list of all item sets with $\mathbf{Support}≥minsupp$.
- Association rule generation: Generate all association rules with $\mathbf{Confidence}≥minconf$.

### Apriori algorithm
![[Skærmbillede 2023-12-02 kl. 21.46.44.png]]
