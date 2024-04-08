---
title: Formatting problems
teaching: 20
exercises: 0
---

::::::::::::::::::::::::::::::::::::::: objectives

- Recognise and resolve common spreadsheet formatting problems.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- What are some common challenges with formatting data in spreadsheets and how can we avoid them?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Common Spreadsheet Errors

This episode is used as a reference for discussion as learners identify issues with the messy dataset discussed in the
previous episode. 

Instructors: don't go through this episode except to refer to responses to the exercise in the previous episode.

- [Common Spreadsheet Errors](#common-spreadsheet-errors)
- [Using multiple tables {#tables}](#using-multiple-tables-tables)
- [Using multiple tabs {#tabs}](#using-multiple-tabs-tabs)
- [Adding column headers into your data {#headers}](#adding-column-headers-into-your-data-headers)
- [Not filling in zeros {#zeros}](#not-filling-in-zeros-zeros)
- [Using problematic null values {#null}](#using-problematic-null-values-null)
- [Using formatting to convey information {#formatting}](#using-formatting-to-convey-information-formatting)
- [Using formatting to make the data sheet look pretty {#formatting-pretty}](#using-formatting-to-make-the-data-sheet-look-pretty-formatting-pretty)
- [Placing comments or units in cells {#units}](#placing-comments-or-units-in-cells-units)
- [Entering more than one piece of information in a cell {#info}](#entering-more-than-one-piece-of-information-in-a-cell-info)
- [Using problematic variable names {#variable-name}](#using-problematic-variable-names-variable-name)
- [Using special characters in data {#special}](#using-special-characters-in-data-special)
- [Inclusion of metadata in data table {#metadata}](#inclusion-of-metadata-in-data-table-metadata)

## Using multiple tables {#tables}

Creating multiple tables within one spreadsheet might seem convenient, but:

- you won't be able to import the data into specialised analyses software because it confuses the computer.

![](fig/2_datasheet_example.jpg){alt='multiple tabs'}

In the example above, the computer will see (for example) row 4 and assume that all columns A-AF refer to the same sample. This row actually represents four distinct samples.

## Using multiple tabs {#tabs}

Creating multiple spreadsheets in separate tabs might seem convenient, but:

- you're more likely to accidentally add inconsistencies if your data is split between multiple tabs
- you'll need to combine the data into a single table to analyse them together anyway. 

If the tabs are inconsistently formatted, you might have to combine them manually. Better to add different dates as a variable within a single unified table. Before adding a tab ask yourself if it's actually a new column you need to add. 

## Adding column headers into your data {#headers}

Your data sheet might get very long over the course of your work. This makes it harder to enter data if you can't see your headers at the top of the spreadsheet. But don't repeat your header row. These can easily get mixed into the data,
leading to problems down the road.

Instead you can freeze the column headers so that they remain visible even when you have a spreadsheet with many rows.

[How to freeze column headers in MS Excel](https://support.microsoft.com/en-au/office/freeze-panes-to-lock-rows-and-columns-dab2ffc9-020d-4026-8121-67dd25f2508f)

## Not filling in zeros {#zeros}

There is a very important difference between a zero and a blank cell in a spreadsheet. To the computer, a zero is actually data that you measured or counted, whereas a blank cell means that it wasn't measured and will be interpreted as an unknown (or 'null') value.

Spreadsheet or statistical software will likely misinterpret blank cells if you intend them to be zeros. By not entering the value of your observation, you are telling your computer to represent that data as unknown or missing (null). This can cause problems with subsequent calculations or analyses. For example, when averaging a set of numbers, null values are excluded, because the computer can't guess the value of the missing observation. Because of this, it's very important to record zeros as zeros and truly missing data as blank cells.

## Using problematic null values {#null}

There are many reasons why null values are represented differently within a dataset. Sometimes confusing null values are automatically recorded from the measuring device. If that's the case, there's not much you can do, but it can be addressed in data cleaning with a tool like OpenRefine before analysing or sharing. In other cases, null values are used to convey different reasons why the data is missing. This is important information to capture, but instead of using one column to capture two pieces of information, it would be better to create a new column like 'data\_missing' and use that column to capture the different reasons.

For missing data, blank cells are usually the best choice.

## Using formatting to convey information {#formatting}

Sometimes people use formatting to convey information which should be captured elsewhere. For example:
- highlighting cells, rows, or columns that should be excluded from an analysis 
- leaving blank rows to indicate separations in data

![](fig/formatting.png){alt='formatting'}

A better solution is to create a new column to encode which data should be excluded.

![](fig/good_formatting.png){alt='good formatting'}

## Using formatting to make the data sheet look pretty {#formatting-pretty}

Sometimes people use formatting to make the spreadsheet look nice. For example, by merging cells. But this will make your data unreadable by statistical software.

## Placing comments or units in cells {#units}

If you need a way to incorporae important notes about certain data in the spreadsheet, create a new column to identify observations which may be suspect. You can put information such as units or calibration information within your README.

## Entering more than one piece of information in a cell {#info}

Don't include more than one piece of information in a cell. This will limit the ways in which you can analyse your data. If you need both these measurements, design your data sheet to include this information. For example, include one column for number of individuals and a separate column for sex.

## Using problematic variable names {#variable-name}

Choose descriptive variable/column names, and be careful not to include spaces, numbers, or special characters of any kind. Spaces can be misinterpreted by parsers that use whitespace as delimiters and some programs don't like field names that are text strings that start with numbers.

Consider using 'lower_snake' case (lower case words separated by underscores) for variable/column names.

Remember to define your variable names and state the units in your README file.

## Using special characters in data {#special}

Avoid copying data directly from Word or other applications, because line breaks, em-dashes, formatting and non-standard characters (such as left- and right-aligned quotation marks) are included. When exporting this data into a coding/statistical environment or into a relational database, dangerous things may occur, such as lines being cut in half and encoding errors being thrown.

General best practice is to avoid adding characters such as newlines, tabs, and vertical tabs. In other words, treat a text cell as if it were a simple web form that can only contain text and spaces.

## Inclusion of metadata in data table {#metadata}

Recording data about your data ("metadata") is essential. You may be on intimate terms with your dataset while you are collecting and analysing it, but the chances that you will still remember that the variable "sglmemgp" means single member of group, for example, or the exact algorithm you used to transform a variable or create a derived one, after a few months, a year, or more are slim.

There are many reasons other people may want to examine or use your data - to understand your findings, to verify your findings, to review your submitted publication, to replicate your results, to design a similar study, or even to archive your data for access and re-use by others. While digital data are usually in some way machine-readable, understanding their meaning is a job for human beings. The importance of documenting your data during the collection and analysis phase of your research cannot be overestimated, especially if your research is going to be part of the scholarly record.

However, metadata should not be contained in the data file itself. Rather, metadata should be stored in a separate file. A common convention is to create a plain text file (.txt) called README.txt and store this kind of contextual information about your data inside it. You can include project details such as authors, funders, abstract, as well as comments, units, information about how null values are encoded, and other information which is important to document but can disrupt the formatting of your data file.

:::::::::::::::::::::::::::::::::::::::: keypoints

- Avoid using multiple tables within one spreadsheet.
- Avoid spreading data across multiple tabs.
- Record zeros as zeros.
- Use an appropriate null value to record missing data.
- Don't use formatting to convey information or to make your spreadsheet look pretty.
- Place comments in a separate column.
- Record units in column headers.
- Include only one piece of information in a cell.
- Avoid spaces, numbers and special characters in column headers.
- Avoid special characters in your data.
- Record metadata in a separate plain text README file.

::::::::::::::::::::::::::::::::::::::::::::::::::


