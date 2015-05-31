## The R directory

### Individual R scripts

This directory contains the R scripts used for the data preparation, analysis and producing figures.
I try to organize each script in chronological order (in the data processing-analysis chain dimension), and name them starting with a number. So that I have something like.
- 1-remoteSensing-pp.R
- 2-inSitu-pp.R
- 3-extract-RS.R
- 4-figure-scatterPlot.R
- etc

As this part of the project tends to grow organically, there might be a need to re-organize it once or twice along the process; surely this takes a bit of time, but will save you even more time later on.

### Sourcing functions

The present directory only contains scripts, no functions. Functions are in `/R/R/` and be sourced as follows:

```r
source('R/R/funName.R')
```

### Small data

Most small data (data.frames, small spatial*DataFrames, etc) are stored in `.rds` files, which is the R way of archiving variables. These `.rds` files are in the `/data/` directory.

To read data:

```r
var <- readRDS('data/filename.rds')
```

To write data:

```r
saveRDS(var, 'data/filename.rds')
```

Only commit small files, big files are stored outside of the project.

### Bigger data

Big raster files, or other voluminous datasets remain outside of the project, on disk, and should not be added to the version control system. However, since we set a `path` variable in the `.Rprofile`, paths to datasets can quickly be constructed using the `file.path()` command.
for instance, to open a `ndvi.grd` file located in the `in/` directory of the external data archive, simply use:

```r
raster(file.path(path, 'in/ndvi.grd'))
```

### Exporting figures
Most figures are produced directly from R, and can be saved (using `ggsave()` for instance). If a figure is manuscript ready, save it directly under `/latex/figs/figureName.eps` so that the figure is directly where it is required to be and does not need to be moved manually.
If a figure requires manual editing, export it first to `/step/`, and work on it there.

So, to export a manuscript ready figure:

```r
ggsave(ggName, filename = 'latex/figs/figureName.eps', width = 7, height = 7)
# Setting width and height is quite important
```
