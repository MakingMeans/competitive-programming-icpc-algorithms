# Notebook Algoritmos ICPC (Python)

Proyecto LaTeX (clase IEEEtran, dos columnas) para documentar algoritmos verificados en juez,
pensado para imprimirse y usarse como material de referencia en competencias ICPC.

## Estructura

- `main.tex`: documento principal; solo incluye estilos y capítulos.
- `styles/`
  - `packages.tex`: paquetes (babel español, listings, hyperref…) y símbolos Unicode permitidos en texto.
  - `colors.tex`: paleta de colores.
  - `commands.tex`: comandos propios y **convenciones de escritura** (`\bigO{}`, `\ten{}`, `\pow{}{}`, `\aprox{}`, `\graybold{}`…). Leer la cabecera antes de escribir una entrada.
  - `listings.tex`: estilo del código Python (incluye `literate` para tildes/ñ/flechas dentro del código).
  - `layout.tex`: pie de página con número, espaciado de ecuaciones, metadatos del PDF.
- `sections/NN_capitulo.tex`: índice de cada capítulo (un `\input` por entrada).
- `sections/NN_capitulo/MM_Tecnica.tex`: una entrada por técnica.
- `templib/`: entradas aún no verificadas o sin depurar; **no se compilan** hasta moverlas a `sections/`.
- `images/`: imágenes (logo de la portada).
- `.github/workflows/latex.yml`: compilación en GitHub Actions; falla si hay cajas desbordadas ≥ 10 pt.

## Formato de una entrada

Título: `Técnica [+ técnica secundaria] (problema corto)`, por ejemplo
`Suffix Array + LCP de Kasai (subcadena repetida más larga)`.

Partes, siempre en este orden y con estas etiquetas:

```latex
\subsection{Técnica (problema corto)}
\graybold{Preguntas guía:}     % itemize con 3-4 preguntas para reconocer cuándo aplica
\graybold{Utilidad:} ...
\graybold{Complejidad:} \bigO{...}
\graybold{Fundamento teórico:} ...~\cite{clave}   % \cite al final del párrafo, si aplica
\graybold{Ejercicio aplicado}

(CSES 1649 — Dynamic Range Minimum Queries) Enunciado resumido...

\graybold{I/O:} ...            % límites, patrón de lectura usado, verificación/tiempos
\graybold{Código solución}
\begin{lstlisting}[language=Python] ... \end{lstlisting}
```

Tras el código puede ir un bloque opcional de variantes:
`\graybold{Extras: qué es} — texto` y, si hace falta, su propio `lstlisting`.

Notación: complejidad siempre con `\bigO{n \log n}`; potencias de diez con `\ten{5}`; otras con
`\pow{2}{k}`; valores aproximados con `\aprox{}0.1s`. Matemática en línea con `$...$`, en display
con `\[ \]` o `align*` (nunca `$$`). Dentro de `$...$` no usar los símbolos Unicode `≤ → −`.

## Referencias

Dos niveles, independientes entre sí:

- **Fuente del problema**: entre paréntesis al inicio del `Ejercicio aplicado`, con el
  formato `(JUEZ ID — Título)`, para poder volver a abrirlo en el juez.
- **Bibliografía**: `ieee.bib` reúne los papers originales de cada algoritmo y las obras de
  consulta general. Se citan con `\cite{clave}` al final del `Fundamento teórico`, y la
  lista se imprime al final del PDF. `latexmk` ejecuta BibTeX automáticamente.

## Compilación local

```bash
latexmk -pdf -file-line-error -interaction=nonstopmode -halt-on-error main.tex
```

Requiere una distribución TeX con `babel-spanish` y los patrones de silabación en español
(MiKTeX y TeX Live los incluyen).

## Overleaf

Subir el proyecto completo comprimido en .zip a Overleaf y configurar `main.tex` como archivo principal.

## GitHub

Al hacer push, GitHub Actions compila el PDF y lo publica como artefacto del workflow.
`main.pdf` también se versiona en el repositorio (marcado como binario en `.gitattributes`).
