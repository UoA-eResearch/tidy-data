---
title: Dates as data
teaching: 10
exercises: 3
---

::::::::::::::::::::::::::::::::::::::: objectives

- Describe how dates are stored and formatted in spreadsheets.
- Demonstrate best practices for entering dates in spreadsheets.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- What is a safe approach for handling dates in spreadsheets?

::::::::::::::::::::::::::::::::::::::::::::::::::

Dates in spreadsheets can be a problem. A spreadsheet application may display dates in a
seemingly correct way (to a human observer) but how it actually handles
and stores the dates behinds the scenes may cause issues. Problems with dates can be compounded by the use of DATE functions within a given spreadsheet program (LibreOffice Calc, Microsoft Excel, OpenOffice, Gnumeric). These functions are usually only compatible within the same
family of products. 

:::::::::::::::::::::::::::::::::::::::::  callout

## Note

Most of the images of spreadsheets in this lesson come
from Microsoft Excel running on a Mac or Windows PC. 
  

::::::::::::::::::::::::::::::::::::::::::::::::::

Excel is famous within the scientific community for turning things that aren't dates into dates. For example, many protein or gene names such as MAR1, DEC1, and OCT4 will automatically be changed into dates by Excel. And once overwritten, the original value of the cell is lost. In fact, a global body in charge of setting nomenclature for genes released [guidelines](https://doi.org/10.1038/s41588-020-0669-3) in 2020 which included "symbols that affect data handling and retrieval" as one of the criteria which should be accounted for, in a nod to ongoing issues with Excel. Microsoft subsequently released an [update](https://insider.microsoft365.com/en-us/blog/control-data-conversions-in-excel-for-windows-and-mac) to Excel in 2023 that allows users to disable automatic data conversion of dates. This serves as an important cautionary tale! 

:::::::::::::::::::::::::::::::::::::::::  callout

## Note

To turn off automatic data conversion for dates in Excel:

- On Windows: File > Options > Data > Automatic Data Conversion > Untick "Convert continuous numbers and letters to date"
- On Mac: Excel > Preferences > Edit > Automatic Data Conversion > > Untick "Convert continuous numbers and letters to date"
  

::::::::::::::::::::::::::::::::::::::::::::::::::

## Preferred date format

Dates are commonly stored in a single column because this seems like the most natural way to record dates. But it can be safer to store dates split into their year, month, and day components in separate columns. When entering or recording data, create each of these columns and place the values for day, month, and year into them. For existing spreadsheets, we can use some of Excel's built-in functions to help us extract each component. 

:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise

Pulling day, month, and year out of dates.

1. Create a tab called `dates` in our messy spreadsheet and copy the 'plot 3' table from the `2014` tab (that contains the problematic dates).
2. Create new columns for day, month, and year, and make sure they are formatted as numbers, not dates.
3. Extract day, month, and year from the dates in the `Date collected` column into new columns. For this we 
can use the following built-in Excel functions:

`YEAR()`

`MONTH()`

`DAY()`

You can see that even though we expected the year to be 2014, the year is actually 2015. What happened here is that the field assistant who collected the data for year 2014 initially forgot to include their data for 'plot 3' in this dataset. They came back in 2015 to add the missing data into the dataset and entered the dates for 'plot 3' without the year. Excel automatically interpreted the year as 2015 - the year the data was entered into the spreadsheet and not the year the data was collected. Thereby, the spreadsheet program introduced an error in the dataset without the field assistant realising.

:::::::::::::::  solution

## Solution

![](fig/solution_exercise_1_dates.png)
{alt='dates, exersize 1' .output}


:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

### Dates are actually stored as integers

Spreadsheet programs can display dates in a variety of ways, but these "features" often allow ambiguity to creep into your data. Ideally, data should be as unambiguous as possible..

![](fig/5_excel_dates_1.jpg){alt="Many formats, many ambiguities"}

Excel stores dates as numbers - see the last column in the above figure. Essentially, it counts the days from a default of December 31, 1899, and thus stores July 2, 2014 as  the serial number 41822.

If you refer to the figure above, you'll see that
there are many ways that ambiguity creeps into your data depending on the format you chose when you enter your data, and if you're not fully aware of which format you're using, you can end up actually entering your data in a way that Excel will badly misinterpret and you will end up with errors in your data that will be extremely difficult to track down and troubleshoot.

:::::::::::::::::::::::::::::::::::::::::  callout

## Note

Before entering dates, preformat the column as 'text' by selecting the column > right click > select 'Format cells' > select 'Text'. This way, however you enter your dates is what will actually be stored in the column. The dates will not be converted into an integer.  

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Treating dates as multiple pieces of data rather than one makes them easier to handle.

::::::::::::::::::::::::::::::::::::::::::::::::::


