# Code and Erratum for *On rank one 2-representations of web categories*

I collected a bit of Mathematica code relevant for the paper *On rank one 2-representations of web categories*
<a href="https://arxiv.org/abs/2303.04264">https://arxiv.org/abs/2303.04264</a> on this page.

The code is in a **.n** file that can be downloaded from this site and you can run it with Mathematica.

An Erratum for the paper *On rank one 2-representations of web categories* can be found at the bottom of the page.

# Contact

If you find any errors in the paper *On rank one 2-representations of web categories* **please email me**:

[dtubbenhauer@gmail.com](mailto:dtubbenhauer@gmail.com?subject=[GitHub]%web-reps)

Same goes for any errors related to this page.

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

# The code

The .n file starts by setting up the stage:

```
(*Matrices for the congruence normal form; dim=size of the matrix \
(for H half of the size) and a=eigenvalue*)
G[dim_] := 
  Table[If[i + j == dim + 1, (-1)^(i + dim), 
    If[i + j == dim + 2, (-1)^(i + dim), 0]], {i, 1, dim}, {j, 1, 
    dim}];
jordanBlock[a_, dim_] := 
  SparseArray[{{i_, i_} :> a, {i_, j_} /; j == i + 1 :> 1}, {dim, 
    dim}];
H[a_, dim_] := 
  ArrayFlatten[{{0, IdentityMatrix[dim]}, {jordanBlock[a, dim], 0}}];
(*The trace condition*)
ToSolve[A_] := Tr[Transpose[A] . Inverse[A]];
(*Direct sum*)
DiSum[A_, B_] := ArrayFlatten[{{A, 0}, {0, B}}];
(*Weighted graphs for G*)
TestNum[a_] := If[Mod[a, 2] == 0, 1, 2];
WeightedG[dim_] := 
  Table[If[i + j == dim + 1, TestNum[i + dim], 
    If[i + j == dim + 2, TestNum[i + dim], 0]], {i, 1, dim}, {j, 1, 
    dim}];
GraphForG[dim_] := 
  AdjacencyGraph[WeightedG[dim], 
   VertexLabels -> Table[i -> Placed[i, Center], {i, 1, dim}], 
   VertexSize -> 0.2, EdgeStyle -> Directive[Thickness[0.0025], Blue],
    VertexLabelStyle -> Directive[20, Blue, Bold], 
   VertexStyle -> Pink, DirectedEdges -> True, ImageSize -> Large];
(*Weighted Graph for H*)
GraphForH[a_, dim_] := 
  AdjacencyGraph[H[a, dim], 
   VertexLabels -> Table[i -> Placed[i, Center], {i, 1, 2*dim}], 
   VertexSize -> 0.2, EdgeStyle -> Directive[Thickness[0.005], Blue], 
   VertexLabelStyle -> Directive[20, Blue, Bold], VertexStyle -> Pink,
    DirectedEdges -> True, ImageSize -> Large];
```

The matrices $G_{dim}$ and $H_{dim}(a)$ are setup and can easily be displayed:

![The G matrices](https://github.com/dtubbenhauer/2-representations-of-webs/blob/main/web-reps1.png)

Most of the code is then pretty standard and hopefully easy to unwrap. The main point is the classification of 
solutions for small $n\in\mathbb{Z}_{\geq 2}$:

![The dimension 3 case](https://github.com/dtubbenhauer/2-representations-of-webs/blob/main/web-reps2.png)

# Erratum

Empty so far.
