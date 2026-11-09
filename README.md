# Cayley’s Formula: Three Proofs and Computational Verification in R

## Overview

This project explores **Cayley’s Formula**, a fundamental result in enumerative combinatorics stating that the number of labelled trees on \(n\) distinct vertices is

\[
T_n=n^{n-2}, \qquad n\geq 2.
\]

The project develops three independent mathematical proofs, each approaching the result from a different perspective:

1. **Prüfer Bijection:** Establishes a one-to-one correspondence between labelled trees and Prüfer sequences of length \(n-2\).
2. **Matrix-Tree Theorem:** Uses determinants of Laplacian matrix minors to count spanning trees of a complete graph.
3. **Laplacian Eigenvalues:** Derives the formula using the eigenvalue structure of the complete graph's Laplacian matrix.

The mathematical arguments are presented in full, followed by computational verification in R.

## Mathematical Objectives

- Establish Cayley's formula through three independent proof techniques.
- Demonstrate the relationship between labelled trees, Prüfer sequences and graph structures.
- Apply the Matrix-Tree theorem to complete graphs.
- Derive the Laplacian eigenvalues of complete graphs and connect them to spanning-tree enumeration.
- Use computational methods to verify theoretical results for finite cases.

## 1. Proof I: Prüfer Bijection

The Prüfer correspondence establishes a bijection between labelled trees on \(n\) vertices and sequences of length \(n-2\), where each element belongs to the vertex set.

Since each of the \(n-2\) positions has \(n\) possible values, the number of sequences is

\[
\underbrace{n\times n\times\cdots\times n}_{n-2\text{ times}}
=n^{n-2}.
\]

The proof establishes:

- Construction of a Prüfer sequence from a labelled tree.
- Reconstruction of a unique labelled tree from a Prüfer sequence.
- The bijective relationship between the two sets.
- The resulting enumeration formula.

## 2. Proof II: Matrix-Tree Theorem

The Matrix-Tree theorem states that the number of spanning trees of a connected graph equals any cofactor of its graph Laplacian matrix.

For the complete graph \(K_n\), the Laplacian matrix is

\[
L=nI_n-J_n,
\]

where \(I_n\) is the identity matrix and \(J_n\) is the all-ones matrix.

Deleting one row and one column gives

\[
L^{(n)}=nI_{n-1}-J_{n-1}.
\]

Using the determinant identity for matrices of this form gives

\[
\det(nI_{n-1}-J_{n-1})=n^{n-2}.
\]

Therefore, the number of spanning trees of \(K_n\) is \(n^{n-2}\).

## 3. Proof III: Laplacian Eigenvalues

The third proof examines the spectrum of the complete graph's Laplacian matrix.

For \(K_n\), the eigenvalues are

\[
0,\quad n,\quad n,\quad \ldots,\quad n,
\]

where the eigenvalue \(n\) has multiplicity \(n-1\).

The spectral form of the Matrix-Tree theorem gives

\[
\tau(K_n)=\frac{1}{n}\prod_{i=2}^{n}\lambda_i.
\]

Substituting the non-zero eigenvalues,

\[
\tau(K_n)=\frac{1}{n}n^{n-1}
=n^{n-2}.
\]

This provides a spectral interpretation of Cayley's formula.

## 4. Computational Verification in R

R is used to independently check the mathematical results for small values of \(n\).

The computational component includes:

- Generating Prüfer sequences.
- Decoding sequences into labelled trees.
- Counting labelled trees for manageable values of \(n\).
- Constructing graph Laplacian matrices.
- Calculating Laplacian eigenvalues.
- Computing Laplacian cofactors and determinants.
- Comparing computational counts with the theoretical value \(n^{n-2}\).

The verification checks the agreement between the combinatorial, determinant-based and spectral approaches.

**Important:** Exhaustive enumeration is computationally feasible only for relatively small values of \(n\), because the number of labelled trees grows rapidly. Larger cases can be checked using the determinant and eigenvalue calculations without enumerating every tree.

## 5. Expected Results

The theoretical number of labelled trees is:

| Number of vertices \(n\) | Cayley's formula \(n^{n-2}\) |
|---:|---:|
| 2 | 1 |
| 3 | 3 |
| 4 | 16 |
| 5 | 125 |
| 6 | 1,296 |
| 7 | 16,807 |
| 8 | 262,144 |
| 9 | 4,782,969 |
| 10 | 100,000,000 |

The R implementation compares its computed results against these theoretical values.

## 6. Project Structure

```text
cayleys-formula/
│
├── README.md
├── proofs/
│   ├── prufer-bijection.pdf
│   ├── matrix-tree-theorem.pdf
│   └── laplacian-eigenvalues.pdf
│
├── R/
│   ├── prufer_encoding.R
│   ├── prufer_decoding.R
│   ├── matrix_tree.R
│   ├── laplacian_spectrum.R
│   └── exhaustive_verification.R
│
├── results/
│   ├── verification_results.csv
│   └── computational_summary.txt
│
└── figures/
    └── graph_visualisations.png
```

*The structure represents the intended organisation of the project; files should be included as they are implemented.*

## 7. Mathematical Significance

Cayley's formula illustrates how the same mathematical result can emerge from different areas of mathematics.

- **Combinatorics:** Bijections and sequence enumeration.
- **Graph Theory:** Spanning trees and graph Laplacians.
- **Linear Algebra:** Matrix determinants and eigenvalue products.
- **Computational Mathematics:** Algorithmic construction, enumeration and verification.

The three proofs demonstrate that combinatorial enumeration, determinant identities and spectral graph theory are closely connected.

## 8. References

1. Cayley, A. (1889). A theorem on trees. *Quarterly Journal of Mathematics*, 23, 376–378.
2. Prüfer, H. (1918). Neuer Beweis eines Satzes über Permutationen. *Archiv der Mathematik und Physik*, 27, 742–744.
3. Kirchhoff, G. (1847). Über die Auflösung der Gleichungen, auf welche man bei der Untersuchung der linearen Vertheilung galvanischer Ströme geführt wird. *Annalen der Physik und Chemie*, 72, 497–508.
4. Godsil, C., & Royle, G. (2001). *Algebraic Graph Theory*. Springer.

## Conclusion

This project presents three complete mathematical proofs of Cayley's formula and uses R to verify their computational consequences. Its central contribution is the demonstration that a single counting identity can be established through a bijective argument, a determinant calculation and a spectral argument.

The emphasis is on mathematical rigour, proof construction and the use of computation as an independent verification tool rather than as a substitute for proof.
