# Introduccion a Rmarkdown

En este apartado estaremos siguiendo el material de Carpentry, capitulo 15 [Producing Reports With knitr](https://swcarpentry.github.io/r-novice-gapminder/15-knitr-markdown/index.html). 

Contenido:

- [1. Informacion basica que compone a un Rmarkdown](#basic)
- [2. Organizacion de la informacion](#organizacion)
- [3. Tipos de formatos generados para reportes con Rmarkdown](#formatos)
- [4. Diferentes lenguajes empleados en Rmarkdown](#lenguajes)
- [5. Visualizacion grafica](#grafica)
- [6. Generar tablas](#tablas)
- [7. Agregar imagenes en un reporte](#imagen)
- [8. Realizar calculos en un texto](#calculo)
- [9. Lenguaje matematico](#mate)
- [10. Agregar notas de ayuda](#note)
- [11. Agregar citas o resaltar texto](#citas)
- [12. Generar indice en el reporte](#indice)

## Requisitos 💻

* Haber instalado Rmarkdown `install.packages('rmarkdown')`
* Instalar LaTeX: Si ya tienen alguna versión de Latex, no hacer nada, Si no tienen instalado Latex, entonces instalar alguna
distribución MiKTeX, MacTeX, and TeX Live o TinyTex:

`install.packages('tinytex')`

`tinytex::install_tinytex()`

`# to uninstall TinyTeX, run`

`# tinytex::uninstall_tinytex()`


## 1. Informacion basica que compone a un Rmarkdown  <a name="basic"></a>

### Archivo inicial

Para crear un archivo dar click en `File/New file/R markdown`. El archivo generado tiene en la parte superior las siguientes instrucciones:

```
---
title: "Introduccion a Rmarkdown"
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

## 2. Organizacion de la informacion <a name="organizacion"></a>

### Division de titulos

Los titulos se dividen por el simbolo `#`, de la siguiente manera:

```
# Genero Plantae (titulo principal)
## Plantas Verdes (sub1)
### Streptophyta (sub2)
#### Plantas terrestres (sub3)
##### Plantas vaculares (sub4)
```

*****
# Genero Plantae (titulo principal)
## Plantas Verdes (sub1)
### Streptophyta (sub2)
#### Plantas terrestres (sub3)
##### Plantas vaculares (sub4)
*****

### Letras en diferentes estilos

Puedes resaltar tu informacion colocando el simbolo `*` antes y despues del texto: Ejemplo: *italica*, **negritas** y ***ambos tipos de estilo***.

```
*italica*
**negritas**
***italica + negritas***
```

### Listas

#### Simple (Una sola division):

```
* one
* two
* three
```

* one
* two
* three

#### Compleja:

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

#### Otro ejemplo:

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

## 3. Tipos de formatos generados para reportes con Rmarkdown <a name="formatos"></a>

Con Rmarkdown puedes generar diversos archivos de salida como son:

* PDF
  - [Tesis ejemplo 1](https://ourcodingclub.github.io/tutorials/rmarkdown-dissertation/)
  - [Tesis ejemplo2](http://destio.us.es/calvo/memoriatfe/MemoriaTFE_PedroLuque_2017Nov_imprimir2caras.pdf) 
  - [Curriculum vitae](https://elipapa.github.io/markdown-cv/) 
* html
  - [Pagina web](https://bookdown.org/yihui/rmarkdown/html-document.html#table-of-contents)
  - [Presentaciones](https://bookdown.org/yihui/rmarkdown/xaringan.html)
* [Word](https://bookdown.org/yihui/rmarkdown/word-document.html)

## 4. Diferentes lenguajes empleados en Rmarkdown <a name="lenguajes"></a>

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

## 5. Visualizacion grafica <a name="grafica"></a>

### Ejemplo que viene por default

En el ejemplo generado con Rmarkdown, presenta el siguiente codigo:

```
plot(pressure)
```  

En la parte superior del chunck, se tiene `echo =FALSE` lo cual oculta el codigo del chunck.

### Ejemplo 2

```
plot(pressure, # dataframe 
    type="b", # Tipo de grafico
    cex=2, # Tamano de los puntos 
    pch = 0, # Forma del punto, valor de 0 a 25, el cero es un cuadrado
    main="My Graph", # titulo
    xlab="The x-axis", ylab="The y axis", # titulo en X y en Y
    col="red") # color de las lineas y puntos
    
# type: 
    # - "p" for points, 
    # - "l" for lines, 
    # - "b" for both, 
    # - "c" for the lines part alone of "b",   
    # - "o" for both ‘overplotted’,
    # - "h" for ‘histogram’ like (or ‘high-density’) vertical lines,
    # - "s" for stair steps,
    # - "S" for other steps, see ‘Details’ below,
    # - "n" for no plotting.

```
Guardar el grafico

```{r, eval=FALSE}
png(file="./pressure.png",  width=15, height=10, units="in", res=1200)

plot(pressure, # dataframe 
    type="b", # Tipo de grafico
    cex=2, # Tamano de los puntos 
    pch = 0, # Forma del punto, valor de 0 a 25, el cero es un cuadrado
    main="My Graph", # titulo
    xlab="The x-axis", ylab="The y axis", # titulo en X y en Y
    col="red") # color de las lineas y puntos

dev.off()
```

Para ver las otras opciones contenidas en la funcion `plot` puedes leer el [manual](https://www.rdocumentation.org/packages/graphics/versions/3.6.2/topics/plot).

Si quieres ver las diferentes formas que puedes hacer en los puntos, puedes leer la [guia](http://www.sthda.com/english/wiki/r-plot-pch-symbols-the-different-point-shapes-available-in-r).

Si quieres realizar otro tipo de grafica puedes visitar la [R graph gallery](https://r-graph-gallery.com/)

### Visualizar el contenido del dataframe

Si queremos analizar la informacion contenida en el dataframe `pressure` podemos emplear la funcion `head()`:

```
head(pressure)
```

Este dataframe contiene dos columnas: `temperature` y `pressure`.

Para ver las estadisticas de esta base de datos usamos `summary`:

```
summary(pressure)
```

## 6. Generar tablas <a name="tablas"></a>

### Tabla simple

```
| Num | Header | Header2 | Header3 |
|-----|--------|---------|---------|
|  1  | first  | 1st     | One     |
|  2  | second | 2nd     | Two     |
|  3  | third  | 3rd     | Three   |
```

| Num | Header | Header2 | Header3 |
|-----|--------|---------|---------|
|  1  | first  | 1st     | One     |
|  2  | second | 2nd     | Two     |
|  3  | third  | 3rd     | Three   |

### Tabla en formato html

```
<table class="table table-hover">
  <thead>
    <tr>
      <th scope="col"><center>Num</center></th>
      <th scope="col"><center>Header</center></th>
      <th scope="col"><center>Header2</center></th>
      <th scope="col"><center>Header3</center></th>
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
```

<table class="table table-hover">
  <thead>
    <tr>
      <th scope="col"><center>Num</center></th>
      <th scope="col"><center>Header</center></th>
      <th scope="col"><center>Header2</center></th>
      <th scope="col"><center>Header3</center></th>
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

## 7. Agregar imagenes en un reporte <a name="imagen"></a>

Podemos anexar imagenes a nuestros archivos tomando figuras de internet como el siguiente ejemplo.

```
![The Carpentries Logo](https://carpentries.org/assets/img/TheCarpentries.svg)
```

![The Carpentries Logo](https://carpentries.org/assets/img/TheCarpentries.svg)

Ademas, podemos anexar archivos contenidos en nuestra computadora:

```
knitr::include_graphics("pressure.png")
```

## 8. Realizar calculos en un texto <a name="calculo"></a>

Podemos senalar en el texto que parte del mismo es un calculo matematico mediante el simbolo de comilla invertida (` `) en ambos extremos. Obteniendo algunos ejemplos como los siguientes.

La suma de 4 mas 5 es `r 4+5`.

La division de 4 entre 5 es `r 4/5`.

La multiplicacion de 4 por 5 es `r 4*5`.

Si 4^5 cuanto es? `r 4^5`

Redondear valores, 9.44 se redondea a `r round(9.44,1)`

## 9. Lenguaje matematico <a name="mate"></a>

* Agregar ecuacion matematica

$$y = \mu + \sum_{i=1}^p \beta_i x_i + \epsilon$$

* Agregar subindices para formulas CO~2~, alternativamente con `html` CO<sub>2</sub>

* Agregar super indice E=MC^2^ o $E=MC^2$, alternativamente con `html` E=MC<sup>2</sup>

## 10. Agregar notas de ayuda <a name="note"></a>

Para dar color a tus reportes puede agregar notas en los mismos dependiendo del contenido de la informacion:

Blue boxes (alert-info)
<div class="alert alert-block alert-info">
<b>Tip:</b> Use blue boxes (alert-info) for tips and notes.</div>

Yellow boxes (alert-warning)
<div class="alert alert-block alert-warning">
<b>Example:</b> Use yellow boxes for examples that are not inside code cells, or use for mathematical formulas if needed. Typically also used to display warning messages.
</div>

Green boxes (alert-success)
<div class="alert alert-block alert-success">
<b>Success:</b> This alert box indicates a successful or positive action.
</div>

Red boxes (alert-danger)
<div class="alert alert-block alert-danger">
<b>Danger:</b> This alert box indicates a dangerous or potentially negative action.
</div>

## 11. Agregar citas o resaltar texto <a name="citas"></a>

### Una sola frase

```
> La belleza pierde su sentido cuando te rodea en exceso. 
```

> La belleza pierde su sentido cuando te rodea en exceso. 

### Un parrafo completo

```
> La belleza pierde su sentido cuando te rodea en exceso.
>
> Pag. 41. El jardin de las mariposas. Dot Hutchison.
```

> La belleza pierde su sentido cuando te rodea en exceso.
>
> Pag. 41. El jardin de las mariposas. Dot Hutchison.

### Hacer mas compleja la cita

```
> La belleza pierde su sentido cuando te rodea en exceso. 
>
>> La belleza depende de los ojos que la miran.
```

> La belleza pierde su sentido cuando te rodea en exceso. 
>
>> La belleza depende de los ojos que la miran.

### Agregar elementos

```
> #### Cosas por hacer:
>
> - Github de la clase de Rmarkdown.
> - Github de la clase de RNA-Seq.
> - Informacion de la pagina de JAGUAR.
>
>  *Todo* va de acuerdo a lo **planeado**.
```

> #### Cosas por hacer:
>
> - Github de la clase de Rmarkdown.
> - Github de la clase de RNA-Seq.
> - Informacion de la pagina de JAGUAR.
>
>  *Todo* va de acuerdo a lo **planeado**.

## 12. Generar indice en el reporte <a name="indice"></a>

Para finalizar podemos agregarle un indice a nuestro reporte editando la parte superior.

 * Informacion incial
```
---
title: "Introduccion a Rmarkdown"
author: "Evelia Coss"
date: "2023-01-30"
output: html_document
---
```

* Informacion modificada para agregar el indice

```
title: “Introduccion a Rmarkdown”
author: "Evelia Coss"
date: "2023-01-30"
output: 
  html_document:
    toc: yes
    toc_float: yes
    toc_depth: 6
    theme: cerulean
```

* `toc` es para indicar que vas a agregar un indice en el reporte. 
* `toc_float` es para indicar si el indice va a ser flotante o no, si indicas `yes` el indice se localizara a la izquiera de la pantalla y la informacion se desplegara cuando se coloques sobre ella. 
* `toc_depth` es para indicar el numero de subtitulos que puedes tener en el archivo.
* `theme` es la decoracion del archivo.

Para mas temas puedes entrar al siguiente link: https://www.datadreaming.org/post/r-markdown-theme-gallery/

-------------------------------
# Referencias 📚

- [bookdown: Authoring Books and Technical Documents with R Markdown](https://bookdown.org/yihui/bookdown/)

- [bookdown: R Markdown: The Definitive Guide](https://bookdown.org/yihui/rmarkdown/)

- [The Comprehensive LaTeX Symbol List](http://tug.ctan.org/info/symbols/comprehensive/symbols-a4.pdf)

- [Create Awesome LaTeX Table with knitr::kable and KableExtra](https://haozhu233.github.io/kableExtra/awesome_table_in_pdf.pdf)

- [Cpitulo 15 Software Carpentry](https://swcarpentry.github.io/r-novice-gapminder/15-knitr-markdown/index.html)

- [Pandoc's Markdown](https://pandoc.org/MANUAL.html#pandocs-markdown)

- [RMarkdown manual](https://rmarkdown.rstudio.com/lesson-1.html)

- [Basic Syntax](https://www.markdownguide.org/basic-syntax/)

- [Apuntes sobre Markdown](https://support.squarespace.com/hc/es/articles/206543587-Apuntes-sobre-Markdown)

- [Markdown Basics](http://www.ece.ualberta.ca/~terheide/rmarkdown-how-to/markdown.html)

