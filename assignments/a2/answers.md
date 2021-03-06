---
title: CSC 320 A2
author: Andrew Hobden (V00788452)
---

## Question 1

### Q1.a

$$ \text{Non-accept: } \{ q_0, q_3, q_4 \} \text{ Accept: } \{ q_1, q_2, q_5 \} $$
$$ \text{Non-accept: } \{ q_0 \} \{ q_3, q_4 \} \text{ Accept: } \{ q_1, q_2, q_5 \} $$
$$ \text{Non-accept: } \{ q_0 \} \{ q_3, q_4 \} \text{ Accept: } \{ q_1, q_2 \} \{ q_5 \} $$

![](img/q1-min.png)\


### Q1.b

The language recognized by this automataton is:

$$ \{ \omega \in \{0,1\}^* : \omega \text{ is of length 1 or } \omega \text{ is of length 3 or more. } \} $$

## Question 2

### Q2.a

$$ \{ 0^n10^n | m,n \geq 0 \} $$

Noting the pumping length is $p$.

$$ \omega = 0^p10^p $$

We know $|xy| \leq p$, so:

$$ x=0^e, y=0^f, z=10^p $$

$$ \omega = xy^0z = 0^{p-f} (0^f)^0 1 0^p = 0^{p-f} 1 0^p \notin L $$

Since the string does not contain enough $0$'s at the start, this is not regular.

### Q2.b

$$ \{ 0^m1^n | m \neq n \} $$

Noting the pumping length is $p$, choosing an $\omega$ with $n=1$.

$$ \omega = 0^p1 $$

We know $|xy| \leq p$, so:

$$ x=0, y=0^{p-1}, z=1 $$

$$ \omega = xy^0z = 0(0^{p-1})^0 1 = 01 \notin L $$

Since the string has an equal $m$ and $n$ values this is not regular.

### Q2.c

$$ \{ wtw | w,t \in \{0,1\}^* \} $$

Noting the pumping length is $p$, choosing an $\omega$:

$$ \omega = (01)^p (111) (01)^p $$

We know $|xy| \leq p$, so:

$$ x=(01)^{p-e}, y=(01)^{p-f}, z=(111)(01)^p $$

$$ \omega = xy^0z = (01)^{p-e} (111)(01)^p \notin L $$

Since the string does not contain two $w$ pieces this is not regular.

## Question 3

### Q3.a

$$ \{ \omega \in \{0,1\}^* | \omega = \omega^R \} $$

$$ G_{rev} = (\{P\},\{0,1\},A,P) $$

The grammar rules are:

$$ P \rightarrow \epsilon $$
$$ P \rightarrow 0 $$
$$ P \rightarrow 1 $$
$$ P \rightarrow 0P0 $$
$$ P \rightarrow 1P1 $$

### Q3.b

$$ \{ \omega \in \{0,1\}^* | \omega \text{ contains the same number of 0s and 1s.} \} $$

$$ G = (\{P\},\{0,1\},A,P) $$

The grammar rules are:

$$ P \rightarrow \epsilon $$
$$ P \rightarrow 01P $$
$$ P \rightarrow 10P $$
$$ P \rightarrow 1P0 $$
$$ P \rightarrow 0P1 $$

### Q3.c

$$ \{ \omega \in \{0,1\}^* | \omega = 0^n1^n, n \geq 0 \} $$

$$ G = (\{P\},\{0,1\},A,P) $$

The grammar rules are:

$$ P \rightarrow \epsilon $$
$$ P \rightarrow 0P1 $$

## Question 4

$$ A = \{ a^i b^j c^k | i=j \text{ or } j=k \text{ where } i,j,k \geq 0 \} $$

$$ S \rightarrow S_1 | S_2 $$
$$ S_1 \rightarrow XC $$
$$ S_2 \rightarrow AY $$
$$ A \rightarrow aA|\epsilon $$
$$ C \rightarrow cC|\epsilon $$
$$ X \rightarrow aXb $$
$$ Y \rightarrow abY $$

This grammar is ambiguous because of $S \rightarrow S_1 | S_2$ which results in differing parse trees.

## Question 5

Noting the terminals `+`, `*`, `num`, `(`, `)`.

$$ E_0 \rightarrow E $$
$$ E \rightarrow E N_1 | T $$
$$ T \rightarrow T N_2 | F $$
$$ N_1 \rightarrow N_{\text{plus}} T $$
$$ N_2 \rightarrow N_{\text{star}} F $$
$$ F \rightarrow N_{\text{open}} G | N_{\text{num}} $$
$$ G \rightarrow E N_{\text{closed}} $$
$$ N_{\text{plus}} \rightarrow + $$
$$ N_{\text{star}} \rightarrow * $$
$$ N_{\text{open}} \rightarrow ( $$
$$ N_{\text{closed}} \rightarrow ) $$
$$ N_{\text{num}} \rightarrow \text{num} $$

## Question 6

Using the grammar given:

$$ E \rightarrow ET | EF | OR $$
$$ T \rightarrow PE $$
$$ F \rightarrow ME $$
$$ R \rightarrow EC $$
$$ E \rightarrow id $$
$$ E \rightarrow num $$
$$ P \rightarrow + $$
$$ M \rightarrow * $$
$$ O \rightarrow ( $$
$$ C \rightarrow ) $$

Checking the string:

$$ \omega = (id + num) * num $$
$$ \omega = \omega_1 \omega_2 \omega_3 \omega_4 \omega_5 \omega_6 \omega_7 $$

|   | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|---|
| 1 | O | - | - | - | E | - | E |
| 2 |   | E | - | E | R | - | - |
| 3 |   |   | P | T | - | - | - |
| 4 |   |   |   | E | R | - | - |
| 5 |   |   |   |   | C | - | - |
| 6 |   |   |   |   |   | M | F |
| 7 |   |   |   |   |   |   | E |




## Question 7

Consider the grammar

$$ A \rightarrow A + A | A - A | a $$

Broken down to CNF it is:

$$ A \rightarrow AB | AC | D $$
$$ B \rightarrow EA $$
$$ C \rightarrow FA $$
$$ D \rightarrow a $$
$$ E \rightarrow + $$
$$ F \rightarrow - $$

However this grammar is still ambiguous. Consider how it might parse:

$$ a + a + a + a - a - a - a + a $$

There are more than one parse trees for this sequence even in CNF form, so it's still ambiguous.
