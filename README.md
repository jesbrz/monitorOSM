
<!-- README.md is generated from README.Rmd. Please edit that file -->

# monitorOSM_GZ <img src='man/figures/logo.png' align="right" height=130/>

<!-- badges: start -->

[![Actualitza i
publica](https://github.com/OSM-Catalan/monitorOSM/actions/workflows/quarto-publish.yml/badge.svg)](https://github.com/OSM-Catalan/monitorOSM/actions/workflows/quarto-publish.yml)
[![pkgdown](https://github.com/OSM-Catalan/monitorOSM/actions/workflows/pkgdown.yaml/badge.svg)](https://github.com/OSM-Catalan/monitorOSM/actions/workflows/pkgdown.yaml)
[![R-CMD-check](https://github.com/OSM-Catalan/monitorOSM/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/OSM-Catalan/monitorOSM/actions/workflows/R-CMD-check.yaml)
[![pre-commit](https://github.com/OSM-Catalan/monitorOSM/actions/workflows/pre-commit.yaml/badge.svg)](https://github.com/OSM-Catalan/monitorOSM/actions/workflows/pre-commit.yaml)
<!-- [![test-coverage](https://github.com/OSM-Catalan/monitorOSM/actions/workflows/test-coverage.yaml/badge.svg)](https://github.com/OSM-Catalan/monitorOSM/actions/workflows/test-coverage.yaml) -->

<!-- badges: end -->

`monitorOSM` é un repositorio usado para supervisar os cambios en [OpenStreetMap](http://www.openstreemap.com)
comparando obxectos con [bases de datos de referencia](https://github.com/jesbrz/monitorOSM/tree/main/data-raw).

Podes ver os informes que se actualizan diariamente en <https://osm-catalan.github.io/monitorOSM>. Os informes dos 
cambios mostran táboas co estado das etiquetas en OSM e nas bases de datos de referencia:

<table class="gmisc_table" style="border-collapse: collapse; margin-top: 1em; margin-bottom: 1em;">
<thead>
<tr>
<th style="font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;">
osm_url
</th>
<th style="font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;">
cambio
</th>
<th style="font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;">
name:gl
</th>
<th style="font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;">
name
</th>
<th style="font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;">
wikipedia
</th>
</tr>
</thead>
<tbody>
<tr style="background-color: #ffffff;">
<td style="padding: .2em; color: #999999; background-color: #ffffff; text-align: center;">
<http://osm.org/node/XXXX>
</td>
<td style="padding: .2em; color: #52854C; background-color: #ffffff; text-align: center;">
\+
</td>
<td style="padding: .2em; color: #52854C; background-color: #ffffff; text-align: center;">
nome en OSM
</td>
<td style="padding: .2em; color: #999999; background-color: #ffffff; text-align: center;">
Sen cambios
</td>
<td style="padding: .2em; color: #52854C; background-color: #ffffff; text-align: center;">
</td>
</tr>
<tr style="background-color: #ffffff;">
<td style="padding: .2em; color: #999999; background-color: #ffffff; border-bottom: 2px solid grey; text-align: center;">
<http://osm.org/node/XXXX>
</td>
<td style="padding: .2em; color: #FC4E07; background-color: #ffffff; border-bottom: 2px solid grey; text-align: center;">
\-
</td>
<td style="padding: .2em; color: #FC4E07; background-color: #ffffff; border-bottom: 2px solid grey; text-align: center;">
nome de referencia
</td>
<td style="padding: .2em; color: #999999; background-color: #ffffff; border-bottom: 2px solid grey; text-align: center;">
Sen cambios
</td>
<td style="padding: .2em; color: #FC4E07; background-color: #ffffff; border-bottom: 2px solid grey; text-align: center;">
gl:Eliminado
</td>
</tr>
</tbody>
</table>

Tamén mostra que conxuntos de cambios teñen etiquetas rotas 
con ligazóns se queres deixar comentarios.


## Engadir novos obxectos ás bases de datos

Se queres engadir obxectos coas súas etiquetas ás bases de datos, podes abrir un
[ticket](https://github.com/OSM-Catalan/monitorOSM/issues) ou podes tentar facer un PR coas instrucións que atoparás
en [aquí](https://osm-catalan.github.io/monitorOSM/data-raw/README.html).

## Paquete de R

A consulta, a comparación con bases de datos de referencia e a representación da web realízanse cun paquete
desde [R](https://cran.r-project.org/) e accións de github. O paquete tamén inclúe funcións para restaurar obxectos de
xeito rápido, pero como proxecto comunitario, é importante tentar falar con usuarios que non estean de acordo coas bases
de datos de referencia. Consulte a [documentación do paquete R] (https://osm-catalan.github.io/monitorOSM/docs/reference/)
para máis detalles.

### Exemplo de restauración

Instala o paquete R:

``` r
# install.packages("devtools")
devtools::install_github("OSM-Catalan/monitorOSM")
```

Restauración das etiquetas `nome` e `wikipedia` das comarcas do País Valenciano:

``` r
library(monitorOSM)

id <- modifica_etiquetes_osm(
  comarques[comarques$regio == "PV", ],
  claus = c("name", "wikipedia"),
  comentari = "Restaura els noms de les comarques dels País Valencià", hashtags = "monitorOSM"
)
```
Devolve o identificador do conxunto de cambios.
