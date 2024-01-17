---
title: Dates as data
teaching: 10
exercises: 3
---

::::::::::::::::::::::::::::::::::::::: objectives

- Describe how dates are stored and formatted in spreadsheets.
- Describe the advantages of alternative date formatting in spreadsheets.
- Demonstrate best practices for entering dates in spreadsheets.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- What are good approaches for handling dates in spreadsheets?

::::::::::::::::::::::::::::::::::::::::::::::::::

Dates in spreadsheets can be a problem. A spreadsheet application may display dates in a
seemingly correct way (to a human observer) but how it actually handles
and stores the dates behinds the scenes may be problematic. Problems with dates can be compounded by the use of DATE functions within a given spreadsheet program (LibreOffice Calc, Microsoft Excel, OpenOffice,
Gnumeric). These functions are usually only compatible within the same
family of products. 

:::::::::::::::::::::::::::::::::::::::::  callout

## Note

Most of the images of spreadsheets in this lesson come
from Microsoft Excel, run on a Mac or on Windows. 
  

::::::::::::::::::::::::::::::::::::::::::::::::::

Excel is famous within the scientific community for turning things that aren't dates into dates. For example,
many protein or gene names such as MAR1, DEC1, and OCT4 will automatically be changed into dates by Excel. And once overwritten, the original value of the cell is lost. In fact, the HUGO Gene Nomenclature Committee, released [guidelines](https://doi.org/10.1038/s41588-020-0669-3) in 2020 which included "symbols that affect data handling and retrieval", in a nod to ongoing issues with Excel. Microsoft subsequently released an [update](https://insider.microsoft365.com/en-us/blog/control-data-conversions-in-excel-for-windows-and-mac) to Excel in 2023 that allows users to disable automatic data conversion of dates. This serves as an important cautionary tale! 

:::::::::::::::::::::::::::::::::::::::::  callout

## Note

To turn off automatic data conversion in Excel:

- On Windows: File > Options > Data > Automatic Data Conversion > Untick "Convert continuous numbers and letters to date"
- On Mac: Excel > Preferences > Edit > Automatic Data Conversion > > Untick "Convert continuous numbers and letters to date"
  

::::::::::::::::::::::::::::::::::::::::::::::::::

## Preferred date format

Dates are commonly stored in a single column because this seems like the most natural way to record dates.
But it's actually much safer to store dates split into their year, month, and day components in separate columns. When entering or recording data, create each of these columns and place the values for day, month, and year into them. For existing spreadsheets, we can use some of Excel's built-in functions to help us. 

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

:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise

Pulling hour, minute and second out of the current time.

Current time and date are best retrieved using the functions `NOW()`, which
returns the current date and time, and `TODAY()`, which returns the current
date. The results will be formatted according to your computer's settings.

1. Calculate the current time using `NOW()-TODAY()` (and format the cell as time).
2. Extract the hour, minute and second from the current time using
  functions `HOUR()`, `MINUTE()` and `SECOND()`.
3. Press `F9` to force the spreadsheet to recalculate the `NOW()` function,
  and check that it has been updated.

:::::::::::::::  solution

## Solution

1. Typing `=NOW()-TODAY()` will result in a decimal value that is not easily human parsable to a clock-based time. You will need to use the strategies in the third part of this challenge to convert this decimal value to readable time.
2. To extract the hour, type `=HOUR(NOW()-TODAY())` and similarly for minute and second.  
  
  

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


### Dates are actually stored as integers

Spreadsheet programs can display dates in a variety of ways, but these "features" often allow ambiguity to creep into your data. Ideally, data should be as unambiguous as possible..

![](fig/5_excel_dates_1.jpg){alt="Many formats, many ambiguities"}

Excel stores dates as numbers - see the last column in the above figure. Essentially, it counts the days from a default of December 31, 1899, and thus stores July 2, 2014 as  the serial number 41822.

If you refer to the figure above, you'll see that
there are many ways that ambiguity creeps into your data depending on the format you chose when you enter your data, and if you're not fully aware of which format you're using, you can end up actually entering your data in a way that Excel will badly misinterpret and you will end up with errors in your data that will be extremely difficult to track down and troubleshoot.

:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise

What happens to the dates in the `dates` tab of our workbook if we save this sheet in Excel (in `csv` format) and then open the file in a plain text editor (like TextEdit or Notepad)? What happens to the dates if we then open the `csv` file in Excel?

:::::::::::::::  solution

## Solution

- Click to the `dates` tab of the workbook and double-click on any of the values in the `Date collected` column. Notice that the dates display with the year 2015.
- Select `File -> Save As` in Excel and in the drop down menu for file format select `CSV UTF-8 (Comma delimited) (.csv)`. Click `Save`.
- You will see a pop-up that says "This workbook cannot be saved in the selected file format because it contains multiple sheets." Choose `Save Active Sheet`.
- Navigate to the file in your finder application. Right click and select `Open With`. Choose a plain text editor application and view the file. Notice that the dates display as month/day without any year information.
- Now right click on the file again and open with Excel. Notice that the dates display with the current year, not 2015.  
  As you can see, exporting data from Excel and then importing it back into Excel fundamentally changed the data once again!  
  
  

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

### Advantages of Alternative Date Formatting

### Storing dates as YEAR, MONTH, DAY {#day}

Storing dates in YEAR, MONTH, DAY format helps to avoid ambiguity. For example, this is a spreadsheet representing insect counts that were taken every few days over the summer:

![](fig/6_excel_dates_2.jpg){alt="So, so ambiguous, it's even confusing Excel"}

If Excel was to be believed, this person had been collecting bugs **in the future**. 

Separate date data into separate fields (day, month, year), which will eliminate any chance of ambiguity.

:::::::::::::::::::::::::::::::::::::::: keypoints

- Treating dates as multiple pieces of data rather than one makes them easier to handle.

::::::::::::::::::::::::::::::::::::::::::::::::::


