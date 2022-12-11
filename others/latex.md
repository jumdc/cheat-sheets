![LaTeX_logo](https://user-images.githubusercontent.com/62952163/206713523-88b58654-567d-4212-b450-c97dc4d00a0c.png)

## Table of content
1. [Compilers](#compilers)
2. [Figures](#fig)
     - [Examples](#fig_ex)
        - [plots](#plots_ex)
3. [Bunch of useful stuff](#random)


## Compilers <a name="compilers"></a>
- pdflatex : simplest compiler 
- xlatex : access to all the fonts installed on the computer
- lualatex : when running heavy compilation 


## Figures <a name="fig"></a>
 **tikz**, **pgfplots** ([Documentation](https://ctan.mines-albi.fr/graphics/pgf/contrib/pgfplots/doc/pgfplots.pdf)).

- Create a separate folder for pictures (.tex files for each figure by itself) & for the data; 
- Some libraries are already included in the packages (Automation, calendar library, ...)
- once the pictures is done : every detail can be change very easily and everything will adjust

♻️ create core figures / graphs and re-use with different data. 

- alignement options 

### Nodes

```latex
\begin{tikzpicture}[every node/.style={font=\footnotesize}]
```

### Examples <a name="fig_ex"></a>
- Do not need to have the env (`begin{} ..`) for a small figure 

```latex
\tikz \draw[thick,rounded corners=8pt]
(0,0) -- (0,2) -- (1,3.25) -- (2,2) -- (2,0) -- (0,2) -- (2,2) -- (0,0) -- (2,0);
```
<img width="100" alt="continous line" src="https://user-images.githubusercontent.com/62952163/206709042-bf772720-6e8b-49d8-b786-0968fc770a68.png">

#### Plots <a name="plots_ex"></a>

 - Simple plot with data

```latex
\begin{tikzpicture}
        \begin{axis}
            \addplot {sin(deg(x))};
        \end{axis}
\end{tikzpicture}  
```

- Difference between `\addplot`, `addplot+ [<options>]`, `\addplot[<options>]`


The distinction is as follows: `\addplot` ... (without options) lets pgfplots select colors, markers
and linestyles automatically (using cycle list). The variant `\addplot+[option]` ... will use the
same automatically determined styles, but in addition it uses hoptionsi. Finally, `\addplot[options]`
(without the +) uses only the manually provided hoptionsi.

- Simple with data from csv 

```latex
\begin{tikzpicture}
    \begin{axis}[
        xlabel=$x$,
        ylabel=$y$
    ]
        \addplot table [x=time, y=acc, col sep=semicolon] {data/test.csv}; %col sep=space|tab|comma|semicolon|colon|braces|&|ampersand, default : space
    \end{axis}
\end{tikzpicture} 
```

with data/test.csv : 

```csv
time;acc
0;0
1;1
2;2
5;5
6;6
7;7
```

- Computing Coordinates with Mathematical Expressions
```
\begin{tikzpicture}
    \begin{axis}
    \addplot+ [
        domain=0:360,
        ] {sin(x)};
    \end{axis}
\end{tikzpicture}
```


## Bunch of useful stuff <a name="random"></a>
- `standalone`
The minimal LaTeX class witth just the object (by default : generates a pdf but can also (create a png with ImageMagic))

- use utf-8 encoding
`usepackage[utf8]{inputenc}`

- always load **babel**
- Useful settings when using *teXlive* and *VSCode* : 
    -  `"latex-workshop.latex.autoBuild.run":"never""`
    -  `"latex-workshop.latex.recipe.default": "pdflatex 🔃"`
    -  main *recipe* in the settings : `latex-workshop.latex.recipes`


