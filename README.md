# Kaiju metagenomics classifier for Sunbeam

## Installation:

With your sunbeam conda environment activated,

1. Clone into your Sunbeam directory:
    ```shell
    git clone https://github.com/sunbeam-labs/sbx_kaiju sunbeam/extensions/sbx_kaiju
    ```
    
2. Add the new config options to your config file:
    ```shell
    cat sunbeam/extensions/sbx_kaiju/config.yml >> my_config.yml
    ```

## Setting up databases

For help building Kaiju databases, see the [Kaiju github repo](https://github.com/bioinformatics-centre/kaiju). To build a database with RefSeq bacteria, viruses, and archea, use the following command:

    ```shell
    makeDB.sh -r -p
    ```

Make sure to edit your config file to set the `nodes_fp`, `names_fp`, and `db_fp` for your shiny new database!

## Usage

This adds a new rule, `all_kaiju`. Specify this as your target to use Kaiju to
classify your decontaminated samples, and add Snakemake's `--use-conda`
option:

    sunbeam run --configfile=sunbeam_config.yml --use-conda all_kaiju

(`--use-conda` will tell Snakemake to automatically maintain a separate conda
environment from Sunbeam for this extension, to avoid any package conflicts.)
