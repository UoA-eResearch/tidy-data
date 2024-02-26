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
seemingly correct way (to a human observer) while actually storing the date in a way that may cause issues.

:::::::::::::::::::::::::::::::::::::::::  callout

## Note

Most of the images of spreadsheets in this lesson come
from Microsoft Excel running on a Mac or Windows PC. 
  

::::::::::::::::::::::::::::::::::::::::::::::::::

Excel is famous within the scientific community for turning things that aren't dates into dates. For example, many protein or gene names such as MAR1, DEC1, and OCT4 will automatically be changed into dates by Excel. And once overwritten, the original value of the cell is lost. In fact, a global body in charge of setting nomenclature for genes released [guidelines](https://doi.org/10.1038/s41588-020-0669-3) in 2020 which included "symbols that affect data handling and retrieval" as one of the criteria which should be accounted for, in a reference to ongoing issues with Excel. Microsoft subsequently released an [update](https://insider.microsoft365.com/en-us/blog/control-data-conversions-in-excel-for-windows-and-mac) to Excel in 2023 that allows users to disable automatic data conversion of these kinds of data into dates. This serves as an important cautionary tale! 

:::::::::::::::::::::::::::::::::::::::::  callout

## Note

To turn off automatic data conversion for dates in Excel:

- On Windows: File > Options > Data > Automatic Data Conversion > Untick "Convert continuous numbers and letters to date"
- On Mac: Excel > Preferences > Edit > Automatic Data Conversion > > Untick "Convert continuous numbers and letters to date"

Note: This will only stop Excel from turning text/number combinations such as MAR4, DEC8, etc into dates. It will not prevent Excel from changing the way dates are interpreted and displayed based on regional settings. See below for more information.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Preferred date format

There are two 'tidy' ways to store dates in spreadsheets.

1. Split between multiple columns, so that the year, month, and day component each get their own column.
2. Within a single column, formatted in accordance with ISO 8601 standard: YYYY-MM-DD.

Let's take a look at the first option and assume you have an existing set of dates in a spreadsheet that you'd like to split up.

:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise

Pulling day, month, and year out of dates.

1. Create a tab called `dates` in our messy spreadsheet and copy the 'plot 3' table from the `2014` tab (that contains the problematic dates).
2. Create new columns for day, month, and year. 
3. Make sure they are formatted as numbers, not dates, by right-clicking the column > format cells > number.
4. Extract day, month, and year from the dates in the `Date collected` column into new columns. For this we 
can use the following built-in Excel functions:

`YEAR()`

`MONTH()`

`DAY()`

You can see that even though we expected the year to be 2014, the year is actually 2015. What happened here is that the field assistant who collected the data for year 2014 initially forgot to include their data for 'plot 3' in this dataset. They came back in 2015 to add the missing data into the dataset and entered the dates for 'plot 3' without the year. Excel automatically interpreted the year as 2015 - the year the data was entered into the spreadsheet and not the year the data was collected. The spreadsheet program introduced an error into the dataset without the field assistant realising.

:::::::::::::::  solution

## Solution

![](fig/solution_exercise_1_dates.png)
{alt='dates, exersize 1' .output}


:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

### Dates are actually stored as integers

Spreadsheet programs can display dates in a variety of ways, but these "features" often allow ambiguity to creep into your data. Ideally, data should be as unambiguous as possible.

![](fig/5_excel_dates_1.jpg){alt="Many formats, many ambiguities"}

Excel stores dates as numbers: see the last column in the above figure. Excel stores dates as a number representing the number of days since December 31, 1899. So July 2, 2014 is stored as 41822 because it is 41,822 days after December 31, 1899.

If you're not fully aware of which date format you're using, you can end up entering your data in a way that Excel will badly misinterpret and you will end up with errors in your data that will be extremely difficult to track down and troubleshoot.

## Single-column Dates

The second "tidy" way to store dates is within a single column, formatted in accordance with ISO 8601 standard: `YYYY-MM-DD`. But actually using this date format in Excel is more challenging than first appears.

For example, take the date `2024-01-13`. When you add this value to a cell inside a new Excel spreadsheet (`.xlsx`) and save the spreadsheet in the same format, the date is overwritten to `13/01/2024`. Similarly, when you add this date to a cell inside a new Excel spreadsheet (`.xlsx`) and save the spreadsheet in a non-Excel format (`.csv`), the date is again overwritten to `13/01/2024`. Even when you create a new non-Excel formatted spreadsheet (`.csv`) and save the file still in `.csv` format, the date is overwritten to 13/01/2024. When you create a new non-Excel formatted spreadsheet (`.csv`), pre-format the column as 'text' (right click the column label > format cells > Text), and enter the date, it will be stored correctly and display correctly. However, when this `.csv` file is opened back up again in Excel the date is reinterpreted by Excel, converted to a number, and overwritten as `13/01/2024`.

Why is Excel doing this? When a spreadsheet is opened in Excel it is automatically converting the date to an integer and changing the date format based on your computer's regional date settings. The **only** way to enter a date as `YYYY-MM-DD` and have it be both stored and displayed correctly in Excel is to change your regional date setting. 

:::::::::::::::::::::::::::::::::::::::::  callout

## Note

To stop Excel overwriting and incorrectly displaying dates in `YYYY-MM-DD` format you need to change Windows region settings. This will also change the display of your date in the taskbar.

- On Windows: Start menu > Region > Additional settings > Date tab > enter 'yyyy-MM-dd' into 'Short Date'

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Treating dates as multiple pieces of data rather than one makes them easier to handle.

::::::::::::::::::::::::::::::::::::::::::::::::::
