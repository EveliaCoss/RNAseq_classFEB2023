# Cursos impartidos

Instructora: Dra. Evelia Coss

Clases para los alumnos de Ciencias Genomicas de la UNAM dentro del programa Bioinformatica y estadistica 2.

## Introduccion a Rmarkdown

Clase programada para el 8 de Febrero del 2023.

### Requisitos 💻

*Antes de la clase debes instalar Rmarkdowm* en Rstudio, este proceso toma tiempo.

```
install.packages("rmarkdown")
```

Si no tienes [Rstudio](https://posit.co/download/rstudio-desktop/) debes instalarlo y su version de R mas actual. 

* Instalar LaTeX: Si ya tienen alguna versión de Latex, no hacer nada, Si no tienen instalado Latex, entonces instalar alguna
distribución MiKTeX, MacTeX, and TeX Live o TinyTex:

```
install.packages('tinytex')
tinytex::install_tinytex()
```
### Referencias 📚

- [bookdown: Authoring Books and Technical Documents with R Markdown](https://bookdown.org/yihui/bookdown/)

- [bookdown: R Markdown: The Definitive Guide](https://bookdown.org/yihui/rmarkdown/)

- [The Comprehensive LaTeX Symbol List](http://tug.ctan.org/info/symbols/comprehensive/symbols-a4.pdf)

- [Create Awesome LaTeX Table with knitr::kable and KableExtra](https://haozhu233.github.io/kableExtra/awesome_table_in_pdf.pdf)

- [Capitulo 15 Producing Reports With knitr- Software Carpentry](https://swcarpentry.github.io/r-novice-gapminder/15-knitr-markdown/index.html)

- [Pandoc's Markdown](https://pandoc.org/MANUAL.html#pandocs-markdown)

- [RMarkdown manual](https://rmarkdown.rstudio.com/lesson-1.html)

- [Basic Syntax](https://www.markdownguide.org/basic-syntax/)

- [Apuntes sobre Markdown](https://support.squarespace.com/hc/es/articles/206543587-Apuntes-sobre-Markdown)

- [Markdown Basics](http://www.ece.ualberta.ca/~terheide/rmarkdown-how-to/markdown.html)

----------------------------------
## Expresión diferencial

Clases programadas para la semana del 21 al 24 de Febrero del 2023.

Instalación de [UBUNTU en Windows](https://learn.microsoft.com/es-es/windows/wsl/install?redirectedfrom=MSDN)

### Requisitos 💻

Programas

* kallisto
* R > 4.0
* RStudio
* Paquetes de R con Bioconductor
  - Biconductor
  - DESeq2
  - edgeR
  - tximport

```
# Instalar Bioconductor
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
BiocManager::install(version = "3.16")

# Paquetes / librerias
paquetes = c("DESeq2", "tximport", "edgeR")
BiocManager::install(paquetes)
```

* Paquetes de R
  - wordcloud (opcional)
  - RColorBrewer (opcional)
  - tidyverse
  - dplyr, stringr

```
install.packages("tidyverse")
installed.packages("wordcloud")
install.packages("RColorBrewer")
install.packages("dplyr")
install.packages("stringr")
```

### Agenda

<table class="table table-hover">
  <thead>
    <tr>
      <th scope="col"><center>Día</center></th>
      <th scope="col"><center>Temas</center></th>
      <th scope="col"><center>Link a presentación</center></th>
      <th scope="col"><center>Práctica</center></th>
    </tr>
  </thead>
  <tbody>
  </tr>
    <tr class="table-light">
      <th scope="row">1</th>
      <td><center>first</center></td>
      <td><center>1st</center></td>
      <td><center>One</center></td>
  </tr>
   </tr>
    <tr class="table-light">
      <th scope="row">2</th>
      <td><center>second</center></td>
      <td><center>2nd</center></td>
      <td><center>Two</center></td>
  </tr>
  </tr>
    <tr class="table-light">
      <th scope="row">3</th>
      <td><center>third</center></td>
      <td><center>3rd</center></td>
      <td><center>Three</center></td>
  </tr>
  </tbody>
</table>


### Referencias 📚
