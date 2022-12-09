# LaTeX

## Table of content
1. [Figures](#fig)
     - [Examples](#fig_ex)
3. [Bunch of useful stuff](#random)



## Figures <a name="fig"></a>
 **tikz** \& **pgfmanuel** are the packages to use ([Documentation](https://ctan.tetaneutral.net/graphics/pgf/base/doc/pgfmanual.pdf)). 

- Create a separate folder for pictures (.tex files for each figure by itself) & for the data; 
- Some libraries are already included in the packages (Automation, calendar library, ...)
- once the pictures is done : every detail can be change very easily and everything will adjust

♻️ create core figures / graphs and re-use with different data. 

- alignement options 

### Examples <a name="fig_ex"></a>
- Do not need to have the env (`begin{} ..`) for a small figure 

```latex
\tikz \draw[thick,rounded corners=8pt]
(0,0) -- (0,2) -- (1,3.25) -- (2,2) -- (2,0) -- (0,2) -- (2,2) -- (0,0) -- (2,0);
```
<img width="101" alt="continous line" src="https://user-images.githubusercontent.com/62952163/206709042-bf772720-6e8b-49d8-b786-0968fc770a68.png">

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

