OPCS 4 XML Generation Tool
==========================

A single script to convert source OPCS-4 files to the formats required for publication and feeding into the crossmap tool.

    Converts CodesAndTitles_YYYYMMDD_2.txt to codes_YYYYMMDD.xml
    Converts MetaData_YYYYMMDD_2.txt to meta_YYYYMMDD.xml
    Converts TOCE_YYYYMMDD_2.xls (or TOCE_YYYYMMDD_2.csv if openpyxl not installed) to toce_YYYYMMDD.xml
    Converts Tabular_YYYYMMDD_2.rtf to BlockStructure_YYYYMMDD.csv (and .xlsx if openpyxl is installed)
    Converts Tabular_YYYYMMDD_2.rtf to ClaML_YYYYMMDD.xml

Installation
------------

It will need to be run in an environment that includes Python 3.x.  Written and tested with
Python 3.12 on a Linux platform but versions from about 3.6/3.7 may also work fine and I suspect using Windows
will also be OK.

Documentation
-------------

The convert-opcs4 command is self-documenting.  Just run it with no parameters and it'll say the following:

```
usage: convert-opcs4 [-h] [-f] [-c] [-m] [-t] [-b] [-l] src [dest]

OPCS-4 conversion utility - version 0.1.0 (11-12-2025)

positional arguments:
  src          Source directory or file
  dest         Destination directory - default as src

options:
  -h, --help   show this help message and exit
  -f, --force  Force overwrite of existing files
  -c, --codes  Convert CodesAndTitles*.txt to codes_YYYYMMDD.xml
  -m, --meta   Convert MetaData*.txt to meta_YYYYMMDD.xml
  -t, --toce   Convert TOCE*.xlsx (or TOCE*.csv) to toce_YYYYMMDD.txt
  -b, --block  Convert Tabular*.rtf to BlockStructure_YYYYMMDD.csv (and .xlsx)
  -l, --claml  Convert Tabular*.rtf to claml_YYYYMMDD.xml

    Convert provided OPCS-4 files to other formats.

    Either specify a source directory containing the files to convert or specify individual files.
    The results will be written to the same directory as the source or to a destination directory or file if specified.

    If no conversion is specified all files in the source directory will be converted.

    The usual M.O. is therefore to put all source files in a directory then just give that directory and a destionation,
    which will be created if it doesn't exist.

    If the openpyxl module is installed then the 'block' conversion will also generate an Excel file.


Error: the following arguments are required: src
```

Individual files can be processed by using the appropriate -c, -m etc. (or --code, --meta...) and specifying either the file or the directory containing it.  The script will try to process the command sensibly.

Running
-------

The simplest method is to load the source files into a single directory then run convert-opcs4 with that directory and
a destionation directory (this will be created if it doesn't exist).

However, currently we can't process the raw TOCE file as an .xls so we need to load it into Excel and save it as a .CSV to convert it to:

- TOCE_410_20220905_1.csv

So, assuming the source directory is called 'source':

```
./convert-opcs4 source dest
```

or on Windows (probably):

```
python convert-opcs4 source dest
```
It only takes a few seconds to run (a few more if openpyxl is installed and the BlockStructure.xlsx file is produced) and
the results will be in 'dest'.


Questions
---------

If you have any questions, currently try emailing the author at roger.jane@nhs.net.
