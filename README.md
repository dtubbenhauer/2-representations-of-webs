# 2-representations-of-webs

I collected a bit of Mathematica code relevant for the paper *On rank one 2-representations of web categories*
<a href="https://arxiv.org/abs/2303.04264">https://arxiv.org/abs/2303.04264</a> on this page.

The code is in a **.n** file that can be downloaded from this site and you can run it with Mathematica.

# Background

The paper *On rank one 2-representations of web categories* is actually about 2-representations, but for the actual calculations 
(or to read this page) **we do not need to know anything about 2-representations**. We rather recall some notions regarding matrices. Our main source for this is
the paper <a href="https://arxiv.org/abs/0709.2473">https://arxiv.org/abs/0709.2473</a>.

Recall matrix congruence $\equiv_{c}$, that is, 
$$\big(A\equiv_{c}B\big)\,\Leftrightarrow\;\big(\exists P\in\mathrm{GL}_{n}(\mathbb{C})\colon A=P^{T}BP\big).$$

A main task asked in the paper *On rank one 2-representations of web categories* is to **classify (up to $\equiv_{c}$)** nondegenerate matrix solutions of
$$\mathrm{tr}(N^{T}N^{-1})=-q-q^{-1}$$
for some complex number $q$. For example, one could take $q=1$ so that
$$\mathrm{tr}(N^{T}N^{-1})=-2$$
is the equation of interest.

In order to do this, let us look at a **Jordan-type normal form** for matrices up to $\equiv_{c}$. 
Let $J_{n}(\lambda)$ denote an n-by-n
(upper triangular) Jordan block with eigenvalue 
$\lambda\in\mathbb{C}$. 
We use $id_{n}$ for the n-by-n identity matrix, and additionally define two 
*new* Jordan blocks:

$$G_{n}=\begin{pmatrix}
& & & (-1)^{n+1} & (-1)^{n}
\\
& & \dots & \dots &
\\
& -1 & -1 & &
\\
1 & 1 & & &
\end{pmatrix}
\text{ and }
H_{2n}(\lambda)=
\begin{pmatrix}
0 & id_{n}
\\
J_{n}(\lambda) & 0
\end{pmatrix}.$$

The following is a normal form 
under $\equiv_{c}$ for 
nondegenerate omplex n-by-n matrices $M\in\mathrm{GL}_{n}(\mathbb{C})$ (there is also a version for degenerate matrices but we do not need it here):

**Theorem (Jordan-type normal form)**

> Every nondegenerate omplex n-by-n is congruent to a direct sum of
> matrices of the form $G_{j}$ or $H_{2k}(\lambda)$ with $\lambda\notin\{0,(-1)^{k+1}\}$
> determined up to $\lambda\leftrightarrow\lambda^{-1}$.
