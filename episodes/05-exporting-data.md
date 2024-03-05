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

Once you have created, collected, or transcribed your raw data and are ready to analyse it, it's best practice to first export/save your data as a plain text format. Why should we do this?

- Proprietary formats like `*.xls` or `*.xlsx` are designed to work with a commercial software application like Excel, whereas plain text formats are designed to be 'open' because virtually any software application can open and work with them. In the future, it is possible that proprietary formats will no longer be supported, or the software to open them may not be as common as it is now.

- Plain text formats are light weight, don't save merged cells or other messy formatting, and therefore result in tidier files with smaller file sizes. This is especially advantageous when working with very large datasets, or large numbers of files.

- Plain text formats are considered 'best practice' for storing research data and so are commonly used across disciplines. Funders, institutions, and publishers are increasingly requiring data to be published in a repository and linked to the peer-reviewed article to increase transparency, trust, and reproducibility. Research data repositories often expect you to upload spreadsheets as plain text files.

In practice, this means taking your completed Excel spreadsheet (in `*.xls` or `*.xlsx` format), or LibreOffice spreadsheet (`.ods`), and saving it as a plain text format like `.csv`, which stands for 'comma separated values'. CSV files are quite literally values separated by commas - you can see this by opening a CSV file in a text editor like Notepad or TextEdit.

Spreadsheet software like Excel and LibreOffice can save to plain text formats like CSV easily, although they may give you a scary-sounding warning when you save in a format other than their 'own' format. You can also open plain text formats in any spreadsheet software too.

To save an Excel file in CSV format:

1. From the top menu select 'File' and 'Save as'.
2. In the 'Format' field, from the list, select 'Comma Separated Values' (`*.csv`).
3. Double check the file name and the location where you want to save it and hit 'Save'.

![](fig/excel-to-csv.png){alt='Saving an Excel file to CSV'}

:::::::::::::::::::::::::::::::::::::::::  callout

## Special characters

By default, Microsoft Excel uses ANSI encoding which causes many special characters to display incorrectly. CSV files saved with UTF-8 encoding should display special characters properly, such as Chinese Characters. To import a .CSV file containing special characters, in Excel navigate to the Data tab > From Text/CSV > select the file and then in the import wizard select 65001 Unicode (UTF-8) from the Encoding dropdown. To save a CSV file with UTF-8 encoding, select 'CSV UTF-8 (Comma delimited)' from the 'Format' field when saving.

::::::::::::::::::::::::::::::::::::::::::::::::::

#### Caveats on commas

In some datasets, the data values themselves may include commas (,). This is particularly true in countries that
use commas as decimal separators. In that case, the software which you use (including Excel) will most likely incorrectly display the data in columns. This is because the commas which are a part of the data values will be interpreted as delimiters between columns.

If you are working with data that contains commas, you likely will need to use another delimiter when working in a spreadsheet. In this case, consider using tabs as your delimiter and working with TSV files. TSV files can be exported from spreadsheet
programs in the same way as CSV files.

:::::::::::::::::::::::::::::::::::::::: keypoints

- Data stored in common spreadsheet formats will often not be read correctly into data analysis software, introducing errors into your data.
- Exporting data from spreadsheets to formats like CSV or TSV puts it in a format that can be used consistently by most programs.

::::::::::::::::::::::::::::::::::::::::::::::::::


