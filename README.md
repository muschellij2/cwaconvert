
<!-- README.md is generated from README.Rmd. Please edit that file -->

# `read.cwa` package

<!-- badges: start -->

[![AppVeyor build
status](https://ci.appveyor.com/api/projects/status/github/muschellij2/read-cwa?branch=master&svg=true)](https://ci.appveyor.com/project/muschellij2/read-cwa)
[![R build
status](https://github.com/muschellij2/read.cwa/workflows/R-CMD-check/badge.svg)](https://github.com/muschellij2/read.cwa/actions)
[![R-CMD-check](https://github.com/muschellij2/read.cwa/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/muschellij2/read.cwa/actions/workflows/R-CMD-check.yaml)
<!-- badges: end -->

The goal of `read.cwa` is to provide functionality to convert ‘Axivity’
‘CWA’ files (<https://axivity.com/>). The data was extracted from
<https://github.com/digitalinteraction/openmovement/>, specifically code
from
<https://github.com/digitalinteraction/openmovement/tree/master/Software/AX3/cwa-convert/c>,
which has the following copyright: \> Copyright (c) 2009-2018, Newcastle
University, UK. All rights reserved.

## Installation

You can install the released version of `read.cwa` from
[CRAN](https://CRAN.R-project.org) with:

``` r
install.packages("read.cwa")
```

And the development version from [GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("muschellij2/read.cwa")
```

## Example

This is a basic example which shows you how to read in a CWA file:

``` r
library(read.cwa)
file = system.file("extdata", "ax3_testfile.cwa.gz", package = "read.cwa")
out = read_cwa(file)
#> Converting the CWA to CSV
#> Reading 147 sectors (offset 0, file 147)...
#> [MD].
#> Wrote 876815 bytes of data (17400 samples).
#>   |                                                                              |=======                                                               |  10%  |                                                                              |==============                                                        |  20%  |                                                                              |=====================                                                 |  30%  |                                                                              |============================                                          |  40%  |                                                                              |===================================                                   |  50%  |                                                                              |==========================================                            |  60%  |                                                                              |=================================================                     |  70%  |                                                                              |========================================================              |  80%  |                                                                              |===============================================================       |  90%  |                                                                              |======================================================================| 100%
#> Reading in the CSV: /var/folders/1s/wrtqcpxn685_zk570bnx9_rr0000gr/T//Rtmpy6HY8X/filea65c7823571b.csv
#> indexing filea65c7823571b.csv [============================] 55.98GB/s, eta:  0s                                                                                
```

``` r
head(out)
#> $data
#> # A tibble: 17,400 × 4
#>    time                    X      Y      Z
#>    <dttm>              <dbl>  <dbl>  <dbl>
#>  1 2019-02-26 10:55:06 0.328  0.984  0.203
#>  2 2019-02-26 10:55:06 0.828 -0.359 -0.375
#>  3 2019-02-26 10:55:06 0.875 -0.391 -0.391
#>  4 2019-02-26 10:55:06 0.891 -0.391 -0.391
#>  5 2019-02-26 10:55:06 0.891 -0.375 -0.391
#>  6 2019-02-26 10:55:06 0.875 -0.359 -0.375
#>  7 2019-02-26 10:55:06 0.875 -0.359 -0.391
#>  8 2019-02-26 10:55:06 0.875 -0.359 -0.406
#>  9 2019-02-26 10:55:06 0.875 -0.359 -0.406
#> 10 2019-02-26 10:55:06 0.891 -0.344 -0.406
#> # ℹ 17,390 more rows
#> 
#> $header
#> $header$uniqueSerialCode
#> [1] 39434
#> 
#> $header$frequency
#> [1] 100
#> 
#> $header$start
#> [1] "2019-02-26 10:55:06 UTC"
#> 
#> $header$device
#> [1] "Axivity"
#> 
#> $header$firmwareVersion
#> [1] 44
#> 
#> $header$blocks
#> [1] 145
#> 
#> $header$accrange
#> [1] 8
#> 
#> $header$hardwareType
#> [1] "AX3"
#> 
#> $header$blockLength
#> [1] 120
#> 
#> 
#> $freq
#> [1] 100
```

``` r
out = read_cwa(file, xyz_only = TRUE)
#> Converting the CWA to CSV
#> Reading 147 sectors (offset 0, file 147)...
#> [MD].
#> Wrote 876815 bytes of data (17400 samples).
#>   |                                                                              |=======                                                               |  10%  |                                                                              |==============                                                        |  20%  |                                                                              |=====================                                                 |  30%  |                                                                              |============================                                          |  40%  |                                                                              |===================================                                   |  50%  |                                                                              |==========================================                            |  60%  |                                                                              |=================================================                     |  70%  |                                                                              |========================================================              |  80%  |                                                                              |===============================================================       |  90%  |                                                                              |======================================================================| 100%
#> Reading in the CSV: /var/folders/1s/wrtqcpxn685_zk570bnx9_rr0000gr/T//Rtmpy6HY8X/filea65ccb93526.csv
#> indexing filea65ccb93526.csv [============================] 125.02GB/s, eta:  0s                                                                                
```

``` r
head(out)
#> $data
#> # A tibble: 17,400 × 4
#>    time                    X      Y      Z
#>    <dttm>              <dbl>  <dbl>  <dbl>
#>  1 2019-02-26 10:55:06 0.328  0.984  0.203
#>  2 2019-02-26 10:55:06 0.828 -0.359 -0.375
#>  3 2019-02-26 10:55:06 0.875 -0.391 -0.391
#>  4 2019-02-26 10:55:06 0.891 -0.391 -0.391
#>  5 2019-02-26 10:55:06 0.891 -0.375 -0.391
#>  6 2019-02-26 10:55:06 0.875 -0.359 -0.375
#>  7 2019-02-26 10:55:06 0.875 -0.359 -0.391
#>  8 2019-02-26 10:55:06 0.875 -0.359 -0.406
#>  9 2019-02-26 10:55:06 0.875 -0.359 -0.406
#> 10 2019-02-26 10:55:06 0.891 -0.344 -0.406
#> # ℹ 17,390 more rows
#> 
#> $header
#> $header$uniqueSerialCode
#> [1] 39434
#> 
#> $header$frequency
#> [1] 100
#> 
#> $header$start
#> [1] "2019-02-26 10:55:06 UTC"
#> 
#> $header$device
#> [1] "Axivity"
#> 
#> $header$firmwareVersion
#> [1] 44
#> 
#> $header$blocks
#> [1] 145
#> 
#> $header$accrange
#> [1] 8
#> 
#> $header$hardwareType
#> [1] "AX3"
#> 
#> $header$blockLength
#> [1] 120
#> 
#> 
#> $freq
#> [1] 100
```

``` r
## basic example code
```
