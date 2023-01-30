# Introduccion a Rmarkdown

En este apartado estaremos siguiendo el material de Carpentry, capitulo 15 [Producing Reports With knitr](https://swcarpentry.github.io/r-novice-gapminder/15-knitr-markdown/index.html). 

Contenido:

- [1. Informacion basica que compone a un Rmarkdown](#basic)
- [2. Tipos de formatos generados para reportes con Rmarkdown](#formatos)
- [3. Diferentes lenguajes empleados en Rmarkdown](#lenguajes)
- [4. Visualizacion grafica](#grafica)
- [5. Generar tablas](#tablas)
- [6. Agregar imagenes en un reporte](#imagen)
- [7. Realizar calculos en un texto](#calculo)
- [8. Lenguaje matematico](#mate)
- [9. Agregar notas de ayuda](#note)
- [10. Generar indice en el reporte](#indice)

## Requisitos 💻

* Haber instalado Rmarkdown `install.packages('rmarkdown')`
* Instalar LaTeX: Si ya tienen alguna versión de Latex, no hacer nada, Si no tienen instalado Latex, entonces instalar alguna
distribución MiKTeX, MacTeX, and TeX Live o TinyTex:

`install.packages('tinytex')`

`tinytex::install_tinytex()`

`# to uninstall TinyTeX, run`

`# tinytex::uninstall_tinytex()`


## 1.- Informacion basica que compone a un Rmarkdown  <a name="basic"></a>

### Archivo inicial

Para crear un archivo dar click en `File/New file/R markdown`. El archivo generado tiene en la parte superior las siguientes instrucciones:

```
---
title: "Sesion de Rmarkdown"
author: "Evelia Coss"
date: "2023-01-30"
output: html_document 
---
```

En donde se indica el nombre del archivo que le dimos al crearlo, el nombre del autor, la fecha y el tipo de archivo de salida. En este caso es un archivo tipo html.

Ademas, se incluyen una serie de instrucciones entre la linea de comandos para obtener el resumen (summary) de la variable cars. Las instrucciones pueden contener un titulo, en este caso "cars".

```
summary(cars)
```

## 2.- Organizacion de la informacion

### Division de titulos

Los titulos se dividen por el simbolo `#`, de la siguiente manera:

```
# Genero Plantae (titulo principal)
## Plantas Verdes (sub1)
### Streptophyta (sub2)
#### Plantas terrestres (sub3)
##### Plantas vaculares (sub4)
```

### Letras en diferentes estilos

Puedes resaltar tu informacion colocando el simbolo `*` antes y despues del texto: Ejemplo: *italica*, **negritas** y ***ambos tipos de estilo***.

```
*italica*
**negritas**
***italica + negritas***
```

### Listas

Simple (Una sola division):

```
* one
* two
* three
```

* one
* two
* three

Compleja:

```
* one
* two
    - 2a
    - 2b
* three
    - 3a
        + 3rd layer
    - 2nd layer
* 1st layer
```

* one
* two
    - 2a
    - 2b
* three
    - 3a
        + 3rd layer
    - 2nd layer
* 1st layer

Otro ejemplo:

```

1) item 10
    a) item 10a
    b) item 10b
2) item 11
    i) item 11a
    i) item 11b
3) item 12
```

1) item 10
    a) item 10a
    b) item 10b
2) item 11
    i) item 11a
    i) item 11b
3) item 12



## 2. Tipos de formatos generados para reportes con Rmarkdown <a name="formatos"></a>

Con Rmarkdown puedes generar diversos archivos de salida como son:

* PDF
  - [Tesis ejemplo 1](https://ourcodingclub.github.io/tutorials/rmarkdown-dissertation/)
  - [Tesis ejemplo2](http://destio.us.es/calvo/memoriatfe/MemoriaTFE_PedroLuque_2017Nov_imprimir2caras.pdf) 
  - [Curriculum vitae](https://elipapa.github.io/markdown-cv/) 
* html
  - [Pagina web](https://bookdown.org/yihui/rmarkdown/html-document.html#table-of-contents)
  - [Presentaciones](https://bookdown.org/yihui/rmarkdown/xaringan.html)
* [Word](https://bookdown.org/yihui/rmarkdown/word-document.html)

## 3. Diferentes lenguajes empleados en Rmarkdown <a name="lenguajes"></a>

* R code 
* Pandoc’s Markdown
* Latex
* html

Dentro de los chunck:
* Rcode

    `x= 'hello, world!'`
    
    `x`

* Bash

    `x=$(echo 'hello, world!')'`
    
    `echo $x`
    
* D3
* Python 
* Rcpp
* SQL
* Stan

## 4. Visualizacion grafica <a name="grafica"></a>

## 5. Generar tablas <a name="tablas"></a>
## 6. Agregar imagenes en un reporte <a name="imagen"></a>
## 7. Realizar calculos en un texto <a name="calculo"></a>

## 8. Lenguaje matematico <a name="mate"></a>

## 9. Agregar notas de ayuda <a name="note"></a>

## 10. Generar indice en el reporte <a name="indice"></a>

# Referencias 📚

- [bookdown: Authoring Books and Technical Documents with R Markdown](https://bookdown.org/yihui/bookdown/)

- [The Comprehensive LaTeX Symbol List](http://tug.ctan.org/info/symbols/comprehensive/symbols-a4.pdf)

- [Create Awesome LaTeX Table with knitr::kable and KableExtra](https://haozhu233.github.io/kableExtra/awesome_table_in_pdf.pdf)

- [Cpitulo 15 Software Carpentry](https://swcarpentry.github.io/r-novice-gapminder/15-knitr-markdown/index.html)

- [Pandoc's Markdown](https://pandoc.org/MANUAL.html#pandocs-markdown)
