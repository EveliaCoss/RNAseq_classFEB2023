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
paquetes = c("DESeq2", "tximport")
BiocManager::install(paquetes)
```

* Paquetes de R
  - RColorBrewer (opcional)
  - tidyverse
  - dplyr, stringr

```
install.packages("tidyverse")
#install.packages("RColorBrewer")
install.packages("dplyr")
#install.packages("stringr")
install.packages("ggrepel")
install.packages("ggplot2")
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
      <td><center>Aspectos generales de RNA-Seq</center></td>
      <td><center>https://github.com/EveliaCoss/RNAseq_classFEB2023/blob/3593a9d29f484aab8dd7fb63ab38a6ea725dc59f/RNA_seq/slides/D1_IntroRNASeq_CosasTecnicas.pdf</center></td>
      <td><center>https://github.com/EveliaCoss/RNAseq_classFEB2023/blob/main/RNA_seq/README.md#practica1</center></td>
  </tr>
   </tr>
    <tr class="table-light">
      <th scope="row">2</th>
      <td><center>Diversos pipeline para Alineamiento, ensamblaje y conteo</center></td>
      <td><center>https://github.com/EveliaCoss/RNAseq_classFEB2023/blob/24cccaa85e8dd653ec503613307650bf1d07c208/RNA_seq/slides/D2_Alineamiento1_sesion.pdf</center></td>
      <td><center>https://github.com/EveliaCoss/RNAseq_classFEB2023/blob/main/RNA_seq/README.md#practica2</center></td>
  </tr>
  </tr>
    <tr class="table-light">
      <th scope="row">3</th>
      <td><center>Importar datos en R, Normalización y Corrección por batch / DEG con DESeq2</center></td>
      <td><center>https://github.com/EveliaCoss/RNAseq_classFEB2023/blob/149ae3f12e30366c982f3cc3418d00af0b1658c1/RNA_seq/slides/D3_Normalizacion_batch_sesion.pdf</center></td>
      <td><center>https://github.com/EveliaCoss/RNAseq_classFEB2023/blob/main/RNA_seq/README.md#practica3</center></td>
  </tr>
    </tr>
    <tr class="table-light">
      <th scope="row">4</th>
      <td><center>DEG con edgeR / Análisis funcional</center></td>
      <td><center>Presentacion4</center></td>
      <td><center>https://github.com/EveliaCoss/RNAseq_classFEB2023/blob/main/RNA_seq/README.md#practica4</center></td>
  </tr>
  </tbody>
</table>


### Referencias 📚

- [Curso 2022](https://github.com/mpadilla905/clase_RNA-seq_LCGEJ2022)
- [Minicurso 2021](https://comunidadbioinfo.github.io/minicurso_abr_2021/)
- [Curso Dra. Selene Fernandez](https://github.com/liz-fernandez/PBI_transcriptomics_2022)
- [Tuxedo workshop](https://github.com/trinityrnaseq/RNASeq_Trinity_Tuxedo_Workshop/wiki)



