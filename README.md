# MTI_report

Generates an HTML single-sample report 

## Requirements

```
numpy
pandas
anndata
scanpy
squidpy
matplotlib
plotly
sklearn
markdown
```

Or use `env.yml` to create conda environment

## Basic Usage

`./sample_report.py -f my_data.h5ad`

Input data should contain a `phenotype` column in `adata.obs`

usage: sample_report.py [-h] -f FILE [-c COLUMN]
                        [--removeMarkers REMOVEMARKERS [REMOVEMARKERS ...]]
                        [--nuclearMarker NUCLEARMARKER] [--resolution RESOLUTION]
                        [--leidenRange LEIDENRANGE [LEIDENRANGE ...]] [--radius RADIUS]

optional arguments:

  -h, --help            show this help message and exit

  -f FILE, --file FILE  anndata h5ad cell feature table

  -c COLUMN, --column COLUMN
                        column name for phenotypes, default is 'phenotype'

  --removeMarkers REMOVEMARKERS [REMOVEMARKERS ...]
                        Patterns to remove markers by. Example: 'DAPI' will remove
                        'DAPI_1','DAPI_2', etc. Markers are removed from adata.X but maintained
                        in raw. default is 'DAPI' 'AF'

  --nuclearMarker NUCLEARMARKER
                        Name of nuclear marker in every cycle for QC purposes, default is 'DAPI'

  --resolution RESOLUTION
                        Image resolution in microns/px for density calculation (default is 0.65
                        micron/px)

  --leidenRange LEIDENRANGE [LEIDENRANGE ...]
                        list of resolutions to test (default is just [0.5,0.6])

  --radius RADIUS       Radius (pixels) for neighborhood search (default is 30px)


## Output

In the current working directory, `sample_report.py` will produce:

```
- figures (dir)
- output anndata file (basename_analyzed.h5ad)
- HMTL report with selected figures (basename_report.html)
```

Between runs, rename or delete `figures` dir