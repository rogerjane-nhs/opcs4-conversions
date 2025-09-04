OPCS 4 XML Generation Tool
==========================

Creates the three XML files for an OPCS 4.xx release using the text files and .xls files
that comprise the non-XML release.

Installation
------------

It will need to be run in an environment that includes Python 3.x.  Written and tested with
Python 3.7 on a Linux platform but 3.6 will probably work fine and I suspect using Windows
will also be OK.

Documentation
-------------

There are two components, one to produce the files and the other to provide a load test (i.e.
that the XML is correctly formed) and show counts of the number of elements and attributes.


Running
-------

The source files are (for OPCS 4.10):

- CodesAndTitles_20220905_1.txt
- MetaData_20220905_1.txt
- TOCE_410_20220905_1.xls

The TOCE file will need to be loaded into Excel and saved as a .CSV to convert it to:

- TOCE_410_20220905_1.csv

These filenames are hard-wired into the `opcs-xml` script so that will need editing for later releases.

The `opcs-xml` script runs with no parameters:

```
./opcs-xml
```

or on Windows (probably):

```
python opcs-xml
```

It should take at most a second to run and will produce the following files:

- codes_410.xml
- meta_410.xml
- toce_410.xml

These should be tested using the `load` script as follows (use `python load` in Windows):

```
./load codes_410.xml
./load meta_410.xml
./load toce_410.xml
```

The output should resemble (for toce_410.xml):

```
1        {https://www.digital.nhs.uk/opcs/toce}dsv
9912     {https://www.digital.nhs.uk/opcs/toce}meta
  9912     DESCRIPTION
  9912     OPCS_42
  9912     OPCS_43
  9912     OPCS_44
  9912     OPCS_45
  9912     OPCS_46
  9912     OPCS_47
  9912     OPCS_48
  9912     OPCS_49
  9912     OPCS_410
  429      NOTES
```

This can be compared to previous release by running on a previous release .xml file.

Block Structure File
--------------------

This is created using 'make_block_structure', which reads the Tabular_1_20250829_3.rtf file and outputs
a CSV that can be imported to excel, but also produces a .xlsx file directly if the openpyxl module is installed.

ClaML Version
-------------

Jeremy is keen on a ClaML version, see: https://nhs-my.sharepoint.com/:u:/g/personal/jeremy_rogers_nhs_net/EdDgbFIEoHBAo7QGJrEDGQ8Bk4MAedcpy1kblGcXWFynDQ?e=scuJLy


Questions
---------

If you have any questions, currently try emailing the author at roger.jane@nhs.net.
