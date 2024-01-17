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

- [Using multiple tables](#tables)
- [Using multiple tabs](#tabs)
- [Adding column headers into your data](#headers)
- [Not filling in zeros](#zeros)
- [Using problematic null values](#null)
- [Using formatting to convey information](#formatting)
- [Using formatting to make the data sheet look pretty](#formatting-pretty)
- [Placing comments or units in cells](#units)
- [Entering more than one piece of information in a cell](#info)
- [Using problematic variable names](#variable-name)
- [Using special characters in data](#special)
- [Inclusion of metadata in data table](#metadata)
- [Date formatting](03-dates-as-data.md)

## Using multiple tables {#tables}

A common strategy is creating multiple data tables within
one spreadsheet. It might be convenient for you now, but:

- you won't be able to import the data into specialised analyses software because it confuses the computer.
- you could be using the same variable name in multiple places, which will make it harder to clean your data up
into a usable form. 

The example below depicts the problem:

![](fig/2_datasheet_example.jpg){alt='multiple tabs'}

In the example above, the computer will see (for example) row 4 and assume that all columns A-AF
refer to the same sample. This row actually represents four distinct samples.

## Using multiple tabs {#tabs}

Excel workbooks can hold multiple spreadsheets in separate tabs, which might seem convenient but which actually prevents your data from being tidy.

- you're more likely to accidentally add inconsistencies if your data is split between multiple tabs
- you'll need to combine the data into a single table to analyse them together anyway. If the tabs are inconsistently formatted, you might have to combine them manually. Better to add different dates as a variable within a single unified table.

Before adding a tab ask yourself if it's actually a new column you need to add. 

## Adding column headers into your data {#headers}

Your data sheet might get very long over the course of your work. This makes it harder to enter data if you can't see your headers at the top of the spreadsheet. But don't repeat your header row. These can easily get mixed into the data,
leading to problems down the road.

Instead you can freeze the column headers so that they remain visible even when you have a spreadsheet with many rows.

[Documentation on how to freeze column headers in MS Excel](https://support.office.com/en-ca/article/Freeze-column-headings-for-easy-scrolling-57ccce0c-cf85-4725-9579-c5d13106ca6a)

## Not filling in zeros {#zeros}

There is a very important difference between a zero and a blank cell in a spreadsheet. To the computer, a zero is actually data that you measured or counted, whereas a blank cell means that it wasn't measured and will be interpreted as an unknown (or 'null') value.

Spreadsheet or statistical software will likely misinterpret blank cells if you intend them to be zeros. By not entering the value of your observation, you are telling your computer to represent that data as unknown or missing (null). This can cause problems with subsequent calculations or analyses. For example, when averaging a set of numbers, null values are excluded, because the computer can't guess the value of the missing observation. Because of this, it's very important to record zeros as zeros and truly missing data as blank cells.

## Using problematic null values {#null}

There are many reasons why null values are represented differently within a dataset. Sometimes confusing null values are automatically recorded from the measuring device. If that's the case, there's not much you can do, but it can be addressed in data cleaning with a tool like [OpenRefine](https://www.datacarpentry.org/OpenRefine-ecology-lesson/) before analysing or sharing. In other cases, null values are used to convey different reasons why the data is missing. This is important information to capture, but instead of using one column to capture two pieces of information, it would be better to create a new column like 'data\_missing' and use that column to capture the different reasons.

Blank cells are the best choices for most applications.

## Using formatting to convey information {#formatting}

**Example**: highlighting cells, rows or columns that should be excluded from an analysis, leaving blank rows to indicate separations in data.

![](fig/formatting.png){alt='formatting'}

**Solution**: create a new field to encode which data should be excluded.

![](fig/good_formatting.png){alt='good formatting'}

## Using formatting to make the data sheet look pretty {#formatting-pretty}

**Example**: merging cells.

**Solution**: Formatting a worksheet to be more aesthetically pleasing by merging cells will make your data unreadable by statistics software. Consider restructuring your data in such a way that you will not need to merge cells to organise your data.

## Placing comments or units in cells {#units}

**Example**: Your data was collected, in part, by a summer student who you later found out was misidentifying some of your species, some of the time. You want a way to note these data are suspect.

**Solution**: Most analysis software can't see Excel or LibreOffice comments, and would be confused by comments placed within your data cells. As described above for formatting, create another field if you need to add notes to cells. Similarly, don't include units in cells: ideally, all the measurements you place in one column should be in the same unit, but if for some reason they aren't, create another field and specify the units the cell is in.

## Entering more than one piece of information in a cell {#info}

**Example**: You find one male, and one female of the same species. You enter this as 1M, 1F.

**Solution**: Don't include more than one piece of information in a cell. This will limit the ways in which you can analyse your data.
If you need both these measurements, design your data sheet to include this information. For example, include one column for number of individuals and a separate column for sex.

## Using problematic variable names {#variable-name}

Choose descriptive variable names, and be careful not to include spaces, numbers, or special characters of any kind. Spaces can be misinterpreted by parsers that use whitespace as delimiters and some programs don't like field names that are text strings that start with numbers.

Underscores (`_`) are a good alternative to spaces, or consider writing names in camel case (like this: ExampleFileName). Remember that abbreviations that make sense at the moment may not be so obvious in 6 months, but don't overdo it with names
that are excessively long. Including the units in the field names avoids confusion and enables others to readily interpret your fields. It's useful to add definitions of variables and their units toa README.txt file. 

**Examples**

<table align = "left" style = "width =50%; border: 1px solid black;">
<tr>
	<td> <b>Good Name</b></td> <br />
	<td> <b>Good Alternative </b> </td><br />
	<td> <b>Avoid </b></td><br />
</tr>
<tr>
	<td> Max_temp_C</td>
	<td> MaxTemp </td>
	<td> Maximum Temp (°C) </td>
</tr>
<tr>
	<td> Precipitation_mm</td>
	<td> Precipitation</td>
	<td> precmm </td>
</tr>	
<tr>
	<td> Mean_year_growth</td>
	<td> MeanYearGrowth </td>
	<td> Mean growth/year</td>	
</tr>	
<tr>
	<td> sex </td>
	<td> sex </td>	
	<td> M/F </td>
</tr>
<tr>	
	<td> weight </td>
	<td> weight </td>	
	<td> w.</td>	
</tr>
<tr>	
	<td> cell_type </td>
	<td> CellType </td>
	<td> Cell Type </td>
</tr>
<tr>
	<td> Observation_01 </td>
	<td> first_observation</td>
	<td> 1st Obs</td>
</tr>
</table>

## Using special characters in data {#special}

**Example**: You treat your spreadsheet program as a word processor when writing notes, for example copying data directly from Word or other applications.

**Solution**: This is a common strategy. When writing longer text in a cell, people often include line breaks, em-dashes,
etc in their spreadsheet.  Also, when copying data in from applications such as Word, formatting and fancy non-standard characters (such as left- and right-aligned quotation marks) are included.  When exporting this data into a coding/statistical environment or into a relational database, dangerous things may occur, such as lines being cut in half and encoding errors being thrown.

General best practice is to avoid adding characters such as newlines, tabs, and vertical tabs.  In other words, treat a text cell as if it were a simple web form that can only contain text and spaces.

## Inclusion of metadata in data table {#metadata}

**Example**: You add a legend at the top or bottom of your data table explaining column meaning, units, exceptions, etc.

**Solution**: Recording data about your data ("metadata") is essential. You may be on intimate terms with your dataset while you are collecting and analysing it, but the chances that you will still remember that the variable "sglmemgp" means single member of group, for example, or the exact algorithm you used to transform a variable or create a derived one, after a few months, a year, or more are slim.

There are many reasons other people may want to examine or use your data - to understand your findings, to verify your findings,
to review your submitted publication, to replicate your results, to design a similar study, or even to archive your data for access and re-use by others. While digital data are usually in some way machine-readable, understanding their meaning is a job for human beings. The importance of documenting your data during the collection and analysis phase of your research cannot be overestimated, especially if your research is going to be part of the scholarly record.

However, metadata should not be contained in the data file itself. Unlike a table in a paper or a supplemental file, metadata (in the form of legends) should not be included in a data file since this information is not data, and including it can disrupt how computer programs interpret your data file. Rather, metadata should be stored in a separate file. A common convention is to create a plain text file (.txt) called README.txt and store this kind of contextual information about your data inside it. You can include project details such as authors, funders, abstract, as well as comments, units, information about how null values are encoded, and other information which is important to document but can disrupt the formatting of your data file.

Additionally, file or database level metadata describes how files that make up the dataset relate to each other; what format are they are in; and whether they supercede or are superceded by previous files. 


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


