<!-- README.md is generated from README.Rmd. Please edit that file -->
junr
====

[![Travis-CI Build Status](https://travis-ci.org/FvD/junr.svg?branch=master)](https://travis-ci.org/FvD/junr) [![Coverage Status](https://img.shields.io/codecov/c/github/FvD/junr/master.svg)](https://codecov.io/github/FvD/junr?branch=master) [![CRAN Status Badge](http://www.r-pkg.org/badges/version/junr)](https://cran.r-project.org/package=junr)

Access Open Data in R through the Junar API
-------------------------------------------

The Junar API is the basis for a number of Open Data initiatives in Latin America and the USA. The `junr` package is a wrapper to make it easier to access data made public through the Junar API. Some examples of implementations are listed on the [Junar website](http://www.junar.com/).

### Installation

``` r
install.packages("devtools")
devtools::install_github("FvD/junr")
```

### Usage

For a full example, please consult the [package vignette](http://rpubs.com/FvD/access-junar-api).

**Load the package and set URL and API-Key**

``` r
library(junr)
base_url <- "http://api.datosabiertos.presidencia.go.cr/api/v2/datastreams/"
api_key <- "the-API-Key-from-the-corresponding-url" 
```

With this connection information the `junr` package helps you to do the following:

**Get the index of data behind the base URL**

``` r
get_index(base_url, api_key)
```

You can also just get a list of GUID's `list_guid(base_url, api_key)` or a list of data set titles `list_titles(base_url, api_key)`.

**Get a particular data set**

``` r
data_guid <- "COMPR-PUBLI-DEL-MINIS"
purchasing_data <- get_data(base_url, api_key, data_guid)
```

**Determine data dimensions**

``` r
get_dimensions(base_url, api_key)
```

**Clean up currency data**

``` r
currency_data <- get_data(base_url, api_key, "LICIT-ADJUD-POR-LOS-MINIS")
currency_data$`Monto Adjudicado` <- clean_currency(currency_data$`Monto Adjudicado`)  
```

Accede Datos a través del API de Junar en R
-------------------------------------------

El API de Junar es la base para varias iniciativas de Datos Abiertos en Latino América y los EEUU. El paquete `junr` facilita el acceso a estos datos des R. El objetivo es fomentar el uso de los datos disponibles haciendo el acceso lo mas fácil. Algunos ejemplos de implementaciones se pueden encontrar en el [sitio web de Junar](http://www.junar.com/).

### Instalación

Para instalar este paquete desde Github es necesario tener el paquete `devtools` instalado:

``` r
install.packages("devtools")
devtools::install_github("FvD/junr")
```

### Uso

Para un ejemplo completo por favor consulta la [documentación](http://rpubs.com/FvD/acceder-junar-api).

**Carga el paquete y define el URL y API-Key**

``` r
library(junr)
url_base <- "http://api.datosabiertos.presidencia.go.cr/api/v2/datastreams/"
api_key <- "El-API-Key-que-obtuviste-de-la-pagina"
```

**Obten un indice de los datos detras del URL**

``` r
get_index(url_base, api_key)
```

Para tener solo una lista de los GUID la instrucción puedes usar `list_guid(url_base, api_key)` o para solo un listado de los títulos: `list_titles(url_base, api_key)`

**Obten un conjunto de datos determinado**

``` r
guid_datos <- "COMPR-PUBLI-DEL-MINIS"
datos_compras <- get_data(url_base, api_key, guid_datos)
```

**Determina la cantidad de datos disponibles**

``` r
get_dimensions(url_base, api_key)
```

**Limpiar valores de divisas**

``` r
datos_con_divisas <- get_data(base_url, api_key, "LICIT-ADJUD-POR-LOS-MINIS")
datos_con_divisas$`Monto Adjudicado` <- clean_currency(datos_con_divisas$`Monto Adjudicado`)  
```
