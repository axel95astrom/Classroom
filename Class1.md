Day 2
================
Axel Åström
7 november 2018

``` r
library(tidyverse)
library(magrittr)
Sortiment_hela <- read_csv("Class_files/systembolaget2018-10-08.csv")
Sortiment_hela %<>% 
  mutate(Alkoholhalt = gsub("%","",Alkoholhalt)) %>%
  mutate(Alkoholhalt = as.numeric(Alkoholhalt)) %>%
  mutate(Varugrupp = ifelse(Varugrupp == "Röda","Rött vin",Varugrupp)) %>%
  mutate(Varugrupp = ifelse(Varugrupp == "Vita","Vitt vin",Varugrupp)) 

Dyrast_liter <- Sortiment_hela %>%
  arrange(desc(PrisPerLiter))
head(Dyrast_liter)
```

    ## # A tibble: 6 x 30
    ##       nr Artikelid Varnummer Namn  Namn2 Prisinklmoms Volymiml PrisPerLiter
    ##    <int>     <int>     <int> <chr> <chr>        <dbl>    <dbl>        <dbl>
    ## 1 8.66e6    500119     86615 High~ <NA>         59995      700       85707.
    ## 2 8.29e6   1470235     82915 Smit~ Rare~        57979      700       82827.
    ## 3 8.64e6    500122     86442 High~ <NA>         40995      700       58564.
    ## 4 8.28e6   1203876     82810 Mort~ Rare~        35880      700       51257.
    ## 5 8.52e6   1203870     85217 Stra~ Rare~        34548      700       49354.
    ## 6 8.37e6   2430070     83723 Teel~ 33 Y~        34000      700       48571.
    ## # ... with 22 more variables: Saljstart <date>, Utgått <int>,
    ## #   Varugrupp <chr>, Typ <chr>, Stil <chr>, Forpackning <chr>,
    ## #   Forslutning <chr>, Ursprung <chr>, Ursprunglandnamn <chr>,
    ## #   Producent <chr>, Leverantor <chr>, Argang <int>, Provadargang <chr>,
    ## #   Alkoholhalt <dbl>, Sortiment <chr>, SortimentText <chr>,
    ## #   Ekologisk <int>, Etiskt <int>, Koscher <int>,
    ## #   RavarorBeskrivning <chr>, Pant <dbl>, EtisktEtikett <chr>
