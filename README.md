[![python-tests](https://github.com/haniffalab/webatlas-pipeline/actions/workflows/tests-python.yml/badge.svg)](https://github.com/haniffalab/webatlas-pipeline/actions/workflows/tests-python.yml)
[![codecov](https://codecov.io/gh/haniffalab/webatlas-pipeline/branch/main/graph/badge.svg?token=7HQVFH08WJ)](https://codecov.io/gh/haniffalab/webatlas-pipeline/branch/main)

# WebAtlas Pipeline

[![docs](https://img.shields.io/badge/Documentation-online-blue)](https://haniffalab.github.io/webatlas-pipeline)
[![demo](https://img.shields.io/badge/Demos-view-blue)](https://haniffalab.github.io/webatlas-pipeline/demos.html)
[![doi](https://zenodo.org/badge/DOI/10.5281/zenodo.7405818.svg)](https://doi.org/10.5281/zenodo.7405818)

This Nextflow pipeline processes spatial and single-cell experiment data for visualisation in [webatlas-app](https://github.com/haniffalab/webatlas-app). The pipeline generates data files for [supported data types](http://vitessce.io/docs/data-types-file-types/), and builds a [view config](http://vitessce.io/docs/view-config-json/).


## Usage

The pipeline can handle data from `h5ad` files, image `tif` files, SpaceRanger output, Xenium output and MERSCOPE output. It can also generate image files from data files.

Running the pipeline requires a parameters file that defines configuration options and the data to be processed.
Full instructions and parameters definitions for this files are available in the [documentation](https://haniffalab.com/webatlas-pipeline/setup.html)

A parameters file looks like

```yaml
outdir: "/path/to/output/"

args:
    h5ad:
        compute_embeddings: "True"

projects:
  - project: project_1
    datasets:
      - dataset: dataset_1
        data:
          -
            data_type: h5ad
            data_path: /path/to/project_1/dataset_1/anndata.h5ad
          -
            data_type: raw_image
            data_path: /path/to/project_1/dataset_1/raw_image.tif
          -
            data_type: label_image
            data_path: /path/to/project_1/dataset_1/label_image.tif

vitessce_options:
    spatial:
        xy: "obsm/spatial"
    mappings:
        obsm/X_umap: [0,1]
layout: "simple"
```


The pipeline can then be run like

```sh
nextflow run main.nf -params-file /path/to/run-params.yaml -entry Full_pipeline
```


Parameters file templates are available in the `templates` directory.
