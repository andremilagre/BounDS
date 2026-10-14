# BounDS

**BounDS** is a *Mathematica* notebook that computes tree-level perturbative unitarity bounds
for scalar extensions of the Standard Model.

## What it does

Extra scalar doublets and singlets show up in most BSM models, and in almost all scalar
dark-matter models. Their quartic couplings must satisfy perturbative unitarity, but deriving
these bounds by hand is tedious and error-prone. This is especially true when the model has many
fields or extra symmetries.

With BounDS, you only declare the fields and their symmetries. The notebook then:

- builds the most general quartic potential allowed by those symmetries;
- assembles the 7 independent 2→2 scattering matrices, labelled by |Q,Y,T⟩;
- block-diagonalizes them and returns their eigenvalues Λ. Each eigenvalue must satisfy |Λ| ≤ 8π.

All output can be exported to LaTeX with `TeXForm`.

## Models

BounDS supports any SU(2)<sub>L</sub> × U(1)<sub>Y</sub> model containing:

- `nD` scalar doublets Φ<sub>i</sub>, with Y = 1/2;
- `nc` charged scalar singlets φ<sub>i</sub><sup>+</sup>, with Y = 1;
- `nn` real neutral scalar singlets χ<sub>i</sub>, with Y = 0.

You can add any extra flavour or generalized CP symmetries, whether discrete or continuous, Abelian or non-Abelian.
To include complex neutral singlets, write each one as two real singlets.

## Example: U(1)-symmetric 2HDM

**1. Define the model**

```mathematica
nD = 2; nc = 0; nn = 0;

nSym = 1;
Sym[1] = {
   \[CapitalPhi][1] -> \[CapitalPhi][1],
   \[CapitalPhi][2] -> Exp[I a] \[CapitalPhi][2]
   };
Assume = {a \[Element] Reals};
```

**2. Run** all cells in Step 2 of the notebook.

**3. Inspect the results**

```mathematica
Potential4 // TeXForm
EigenList[0, 0, 0] // FullSimplify // TeXForm
```

Use `Basis[Q, Y, T]` and `ScatteringMatrix[Q, Y, T]` to see the states and the matrix of any channel.

## Citation

If you use BounDS, please cite:

```bibtex
@article{Lopes:2025krb,
    author = "Lopes, Carolina T. and Milagre, Andr{\'e} and Silva, Jo{\~a}o P.",
    title = "{Perturbative unitarity for models with singlet and doublet scalars}",
    eprint = "2510.02434",
    archivePrefix = "arXiv",
    primaryClass = "hep-ph",
    doi = "10.1142/s0217751x26501265",
    journal = "Int. J. Mod. Phys. A",
    volume = "41",
    number = "21",
    pages = "2650126",
    year = "2026"
}
```

## Authors

Carolina T. Lopes, André Milagre, João P. Silva (CFTP, Instituto Superior Técnico, Universidade de Lisboa).
Please report bugs and send questions through [Issues](https://github.com/andremilagre/BounDS/issues).
