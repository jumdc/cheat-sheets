# LaTeX

## Table of content
1. [Figures](#fig)
2. [Bunch of useful stuff](#random)



## Figures <a name="fig"></a>
 **tikz** \& **pgfmanuel** are the packages to use ([Documentation](https://ctan.tetaneutral.net/graphics/pgf/base/doc/pgfmanual.pdf)). 

- Create a separate folder for pictures (.tex files for each figure by itself) & for the data; 
- Some libraries are already included in the packages (Automation, calendar library, ...)
- once the pictures is done : every detail can be change very easily and everything will adjust

### Examples
- Do not need to have the env (`begin{} ..`) for a small figure 
```
\tikz \draw[thick,rounded corners=8pt]
(0,0) -- (0,2) -- (1,3.25) -- (2,2) -- (2,0) -- (0,2) -- (2,2) -- (0,0) -- (2,0);
```

## Bunch of useful stuff <a name="random"></a>
- `standalone`
The minimal LaTeX class witth just the object (by default : generates a pdf but can also (create a png with ImageMagic))

