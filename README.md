Crocket Johnson Inspired Math Art
================

Square Root of Two
------------------

Inspiration [here](https://americanhistory.si.edu/collections/search/object/nmah_694637).

First, let's get a canvas.

``` r
library(tidyverse)
plt <- 
  ggplot() +
  coord_cartesian(
    xlim   = c(-0.5,3.5),
    ylim   = c(-0.5,2.5),
    expand = FALSE
  ) +
  scale_x_continuous(name = '', labels = NULL) +
  scale_y_continuous(name = '', labels = NULL) +
  geom_vline(xintercept = 0:3, size = 1, color = 'black') +
  geom_hline(yintercept = 0:3, size = 1, color = 'black') +
  theme_bw() +
  theme(panel.grid.major = element_blank(),
        panel.grid.minor = element_blank(),
        axis.line        = element_blank(),
        axis.ticks       = element_blank()) 
plt
```

![](README_files/figure-markdown_github/canvas-1.png)

Add some red and blue rectangles

``` r
plt <-
  plt +
  geom_rect(mapping = aes(xmin = 0, xmax = 2, 
                          ymin = 0, ymax = 2),
            alpha   = 0.5,
            fill    = 'red',
            color   = 'black', 
            size    = 1) +
  geom_rect(mapping = aes(xmin = 2, xmax = 3, 
                          ymin = 0, ymax = 2),
            alpha   = 0.5,
            fill    = 'blue',
            color   = 'black', 
            size    = 1)
plt
```

![](README_files/figure-markdown_github/redblue-1.png)

Next, we need a semi-circle.

``` r
crcl <-
  tibble(
    r = seq(0, 180, 1)*pi/180,
    x = 1.5*cos(r) + 1.5,
    y = 1.5*sin(r)
  )
plt <-
  plt +
  geom_polygon(aes(x = x, y = y), crcl) 
plt
```

![](README_files/figure-markdown_github/semicircle-1.png)

Overlay a transparent rectangle.

``` r
plt <-
  plt +
    geom_rect(mapping = aes(xmin = 0, xmax = 2, 
                          ymin = 0, ymax = 2),
            alpha   = 0.5,
            fill    = 'blue',
            color   = 'black', 
            size    = 1) +
  geom_rect(mapping = aes(xmin = 2, xmax = 3, 
                          ymin = 0, ymax = 2),
            alpha   = 0.5,
            fill    = 'red',
            color   = 'black', 
            size    = 1)
#  geom_rect(mapping = aes(xmin = 0, xmax = 2, 
#                          ymin = 0, ymax = 2),
#            alpha   = 0.5,
#            fill    = 'white',
#            color   = 'black', 
#            size    = 1)
plt
```

![](README_files/figure-markdown_github/rectangle-1.png)
