# pif-ingestor

Script to ingest common data formats to citrination.
It uses an extention architecture to import and evaluate converters defined in other pacakages, e.g. [pif-dft](https://github.com/CitrineInformatics/pif-dft) and [sparks-pif-converters](https://github.com/CitrineInformatics/sparks-pif-converters).

## Installation

Install this ingestor and all known public converters:
```
$ pip install pif-ingestor[all]
```
This will place an executable `pif-ingestor` in your bin directory (or the bin directory of your virtualenv).

### Known public converters
 * [dfttopif](https://github.com/CitrineInformatics/pif-dft) (ingests VASP and Quantum Espresso calculations)

## Usage
```
$ pif-ingestor -h
usage: pif-ingestor [-h] [-d DATASET] [--tags TAGS [TAGS ...]] [-l LICENSE]
                    [-c CONTACT] [-z ZIP] [-t TAR]
                    [--args CONVERTER_ARGUMENTS]
                    path format

Ingest data files to Citrination
positional arguments:
  path                  Location of the file or directory to import
  format                Format of data to import, coresponding to the name of
                        the converter extension

optional arguments:
  -h, --help            show this help message and exit
  -d DATASET, --dataset DATASET
                        ID of the dataset into which to upload PIFs
  --tags TAGS [TAGS ...]
                        Tags to add to PIFs
  -l LICENSE, --license LICENSE
                        License to attach to PIFs (string)
  -c CONTACT, --contact CONTACT
                        Contact information (string)
  -z ZIP, --zip ZIP     Zip to this file
  -t TAR, --tar TAR     Tar to this file
  --args CONVERTER_ARGUMENTS
                        Arguments to pass to converter (as JSON dictionary)
```

## Examples

Convert a VASP file, generating a quality report, and upload it to datasetID 7:
```
$ pif-ingestor B.hR12 dft -d 7 --args='{"quality_report" : true}'
```

## Support

*For users*: check out the [citrination-users](https://groups.google.com/forum/#!forum/citrination-users) google group.

*For developers*: use issues and pull requests.
