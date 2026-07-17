# Notebook Algoritmos ICPC Python

Proyecto LaTeX en formato IEEEtran convertido desde `docs/Notebook Algoritmos ICPC Python.docx`.

## Estructura

- `main.tex`: configuración general, portada, índice e inclusión de capítulos.
- `sections/`: capítulos incluidos desde `main.tex` mediante `\input{}`.
- `styles/`: paquetes, colores, comandos y configuración de `listings`.
- `images/`: imágenes extraídas del documento Word.
- `ieee.bib`: archivo BibTeX para referencias IEEE.
- `.github/workflows/latex.yml`: compilación automática en GitHub Actions.

## Compilación local

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
```

## Overleaf

Sube la carpeta completa `Notebook-ICPC/` a Overleaf y configura `main.tex` como archivo principal.

## GitHub

Al hacer push al repositorio, GitHub Actions compila el PDF automáticamente y publica `main.pdf` como artefacto del workflow.
