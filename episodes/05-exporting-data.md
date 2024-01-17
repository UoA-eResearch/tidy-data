---
title: Exporting data
teaching: 10
exercises: 0
---

::::::::::::::::::::::::::::::::::::::: objectives

- Understand why storing spreadsheet data in universal file formats is best-practise.
- Export data from a spreadsheet to a CSV file.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How can we export data from spreadsheets in a way that is useful for downstream applications?

::::::::::::::::::::::::::::::::::::::::::::::::::

Storing data in default Excel
file formats (`*.xls` or `*.xlsx`) isn't a good idea. Why?

- Because it is a proprietary format, and it is possible that in
  the future, technology won't exist (or will become sufficiently
  rare) to make it inconvenient, if not impossible, to open the file.

- Other spreadsheet software may not be able to open files
  saved in a proprietary Excel format.

- Different versions of Excel may handle data
  differently, leading to inconsistencies.

- Finally, more journals, funders, and institutions require researchers
  to deposit data in a data repository, and most of them don't
  accept Excel formats. It needs to be in one of the formats
  discussed below.

- The above points also apply to other formats such as open data formats used by LibreOffice / Open Office. These formats are not static and do not get parsed the same way by different software packages.

As an example of inconsistencies in data storage, do you remember how we talked about how Excel stores dates earlier? It turns out that there are multiple defaults for different versions of the software, and you can switch between them all. So, say you're
compiling Excel-stored data from multiple sources and there are dates in each file. Excel will interpret them as their own internally consistent serial numbers. But when you combine the data, Excel will take the serial number from the place you're importing it from, and interpret it using the rule set for the version of Excel you're using. Essentially, you could be adding errors to your data, and it wouldn't necessarily be flagged by any data cleaning methods if your ranges overlap.

Storing data in a universal, open, and static format will help to deal with this problem. CSV (comma-separated values) files are plain text files where the columns are separated by commas. The advantages of CSV files over propriatery file formats like Excel or SPSS etc. files are:

- You can open and read a CSV file using just about any software, including plain text editors like TextEdit or NotePad. 
- Data in a CSV file can be easily imported into other formats and software environments, such as SQLite and R. 
- It's a good format to work with for maximum portability and endurance.
- CSV files are simple, lightweight, and don't preserve formatting, highlighting, merged cells, etc.

Most spreadsheet programs can save to delimited text formats like CSV easily, although they may give you a scary-sounding warning when you save in a format other than their 'own' format.

To save a file you have opened in Excel in CSV format:

1. From the top menu select 'File' and 'Save as'.
2. In the 'Format' field, from the list, select 'Comma Separated Values' (`*.csv`).
3. Double check the file name and the location where you want to save it and hit 'Save'.

An important note for backwards compatibility: you can open CSV files in Excel!

![](fig/excel-to-csv.png){alt='Saving an Excel file to CSV'}

## A Note on Cross-platform Operability

By default, most coding and statistical environments expect UNIX-style line endings (ASCII `LF` character) as representing line breaks.  However, Windows uses an alternate line ending signifier (ASCII `CR LF` characters) by default for legacy compatibility with Teletype-based systems.

As such, when exporting to CSV using Excel, it's best to select "Windows comma separated (.csv)" file for compatibility.

#### Caveats on commas

In some datasets, the data values themselves may include commas (,). This is particularly true in countries that
use commas as decimal separators. In that case, the software which you use (including Excel) will most likely incorrectly display the data in columns. This is because the commas which are a part of the data values will be
interpreted as delimiters.

If you are working with data that contains commas, you likely will need to use another delimiter when working in a spreadsheet. In this case, consider using tabs as your delimiter and working with TSV files. TSV files can be exported from spreadsheet
programs in the same way as CSV files. For more of a discussion on data formats and potential issues with commas within datasets see [the discussion page](https://www.datacarpentry.org/spreadsheet-ecology-lesson/discuss/).

#### Special characters

.CSV files saved with UTF-8 encoding should display special characters, such as Chinese Characters. However, by default Microsoft Excel uses ANSI encoding which causes many special characters to display incorrectly. To import such a .CSV file, in Excel navigate to the Data tab > From Text/CSV > select the file and then in the import wizard select 65001 Unicode (UTF-8) from the Encoding dropdown.

:::::::::::::::::::::::::::::::::::::::: keypoints

- Data stored in common spreadsheet formats will often not be read correctly into data analysis software, introducing errors into your data.
- Exporting data from spreadsheets to formats like CSV or TSV puts it in a format that can be used consistently by most programs.

::::::::::::::::::::::::::::::::::::::::::::::::::


