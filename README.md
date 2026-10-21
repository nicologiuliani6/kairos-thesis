# Kairos: a reversible and concurrent language

📄 **[Read the thesis in Italian (PDF)](http://nicologiuliani.site/kairos-thesis/tesi.pdf)**
· **[Read the thesis in English (PDF)](http://nicologiuliani.site/kairos-thesis/thesis.pdf)**,
both rebuilt automatically from `main` on every push.

Bachelor's thesis in Computer Science, University of Bologna
(Dipartimento di Informatica – Scienza e Ingegneria), academic year 2026/2027.

- **Author:** Nicolò Giuliani
- **Supervisor:** Prof. Ivan Lanese

The thesis is written in Italian (`tesi.tex`); the English edition (`thesis.tex`) is a
translation of it and has the same content.

## What it is about

Kairos is a structured imperative language that is both **reversible** and
**concurrent**. Every program can run forwards and backwards, and its inverse
is computed from the program text. Kairos builds on the core of Janus
(invertible updates, conditionals and loops with two guards, `call`/`uncall`,
integers and arrays) and adds:

- explicit parallel composition: `par ... and ... rap`;
- synchronous communication on channels (`ssend` / `srecv`), with a binary
  session discipline checked at run time that allows delegation;
- a stack as a primitive data structure;
- transactions with compensation: `try ... rollback ... yrt`.

Parallel branches work on disjoint parts of the store and interact only through
channels. This is the assumption from which confluence of interleavings
follows.

The thesis covers:

1. **Semantics.** A small-step structural operational semantics of Kairos,
   given as an extension of the small-step semantics of Janus by Lami, Lanese
   and Stefani (2024).
2. **Reversibility.** The inversion operator, its correctness, and a check
   against the three sample programs of the original 1982 Janus report.
3. **A case study.** A reversible Burrows–Wheeler transform with blocks
   transformed in parallel, with its cost and the speedup from concurrency.
4. **Implementation.** An interpreter that runs a program one instruction at a
   time, and a debugger that can step forwards and backwards.
5. **Related work and open questions.**

## Repository layout

| File | Content |
|---|---|
| `tesi.tex` | Italian main document: abstract, table of contents, bibliography |
| `frontespizio.tex` | Italian title page |
| `capitoli.tex` | Italian chapters |
| `thesis.tex` | English main document |
| `frontespizio-en.tex` | English title page |
| `capitoli-en.tex` | English chapters |
| `preambolo.tex` | packages and macros (shared; `\linguatesi` selects the language) |
| `refs.bib` | bibliography |
| `img/` | images (university logo) |

## Building

You need a TeX Live installation with `latexmk`, `pdflatex` and `bibtex`. The
document uses, among others, `tikz`/`pgfplots`, `listings`, `natbib`,
`cleveref` and `babel` (Italian and English).

```bash
latexmk -pdf tesi.tex      # produces tesi.pdf (Italian)
latexmk -pdf thesis.tex    # produces thesis.pdf (English)
latexmk -c                 # removes the auxiliary files
```

## Related repositories

- Kairos interpreter and examples:
  <https://github.com/nicologiuliani6/kairos>
- Debugger extension for Visual Studio Code:
  <https://github.com/nicologiuliani6/kairos-vscode-debugger>
