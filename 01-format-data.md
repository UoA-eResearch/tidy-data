---
title: Formatting data tables in Spreadsheets
teaching: 15
exercises: 20
---

::::::::::::::::::::::::::::::::::::::: objectives

- Describe best practices for data entry and formatting in spreadsheets.
- Apply best practices to arrange variables and observations in a spreadsheet.
- Understand the differences between long and wide format data.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How do we properly format data in spreadsheets?

::::::::::::::::::::::::::::::::::::::::::::::::::

Spreadsheets are ubiquitous in research environments, yet many researchers are never taught how to properly format tabular data to ensure it is easy to analyse later. Since most researchers use Excel as their primary spreadsheet software, the rest of this lesson will make use of examples using Excel. Free alternatives including LibreOffice Calc and Google Sheets can be used, but commands and options may differ between software.

### What this lesson will not teach you

- How to do *statistics* in a spreadsheet
- How to do *plotting* in a spreadsheet
- How to *write code* in spreadsheet programs

Doing statistics, plotting data, writing code, and doing in-depth data cleaning are best handled by other software which has been designed for these tasks. Data Carpentry includes lessons on Openrefine and R, which are better suited to performing these kinds of operations.

## Problems with Spreadsheets

Spreadsheet programs like Excel were originally designed to handle the entry, manipulation, and plotting of financial data. It's easy to run into problems when working with research data when we forget Excel's purpose and limitations. For example:

- Be very cautious when opening and saving research data in Excel because by default it automatically reformats certain types of data, and this can introduce major errors (we'll explore an example later when we talk about dates).
- Making tables 'pretty' with merged cells, borders, highlighting, and notes in the margin mean that the data will not be recognised when imported into specialised data analysis software, and will first require time-consuming manual clean up. 
- Statistics and figures generated within 'point and click' software like Excel cannot be reproduced by someone else without detailed instructions, and it's easy to introduce errors when creating plots by hand.

## Structuring Data in Spreadsheets

There are, however, useful things we can do with spreadsheet software to help us
with our research. Ensuring tabular data is consistent and structured in a way that computers understand means we can harness the power of programming languages like R or Python to perform complex analyses with a few lines of code. But to do that, we need to set up our data in a way the computer can understand (and computers are very
literal). 

The number one rule for working with tabular data in spreadsheet software is to keep it "tidy":

1. Put all your variables in columns - the thing you're measuring, like 'weight' or 'temperature'.
2. Put each observation in its own row.
3. Don't combine multiple pieces of information in one cell. You want maximum freedom to sort or subset your data later on.

### Portal Project Teaching Dataset

The data used across the Data Carpentry lessons is a simplified version of the Portal Project Database - a dataset containing observations of rodents in southern Arizona as part of a project studying the effects of rodents and ants on the plant community. The rodents are sampled from a series of 24 plots, with different experimental manipulations controlling which rodents are allowed to access which plots.

The study has been running for almost 40 years and the full dataset has been used in over 100 publications. The data we're going to look at has been simplified a little bit for the workshop, but the full version is available to download if you're interested.  

:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise

We're going to open up a messy version of a spreadsheet containing some of the Portal data. You can get a copy of the spreadsheet [here](https://ndownloader.figshare.com/files/2252083).

You can see that the data is spread across two tabs within this Excel workbook. Let's assume two field assistants conducted the surveys, one in 2013 and one in 2014, and they both kept track of the data in their own way in tabs `2013` and `2014` of the workbook. Let's say you were the person in charge of this project and you wanted to start analysing the data.

In the chat, identify what is wrong with this spreadsheet and what you could do to fix the problem. 

:::::::::::::::  solution

## Solution

- All the mistakes in [02-common-mistakes](02-common-mistakes.md) are present in the messy dataset. As different points are brought up, refer to [02-common-mistakes](02-common-mistakes.md) or expand a bit on the point.
- Note: There is a problem with dates in table 'plot 3' in the `2014` tab. The field assistant who collected the data
  for year 2014 initially forgot to include their data for 'plot 3'. They came back in 2015 to include the missing data and entered the dates for 'plot 3' in the dataset without the year. Excel automatically filled in the missing year as the current year (i.e. 2015) - introducing an error in the data without the field assistant realising. If you get a response from the participants that they've spotted and fixed the problem with date, you can say you'll come back to dates again towards the end of lesson in episode [03-dates-as-data](03-dates-as-data.md). If participants have not spotted the problem with dates in 'plot 3' table, that's fine as you will address peculiarities of working with dates in spreadsheets in episode [03-dates-as-data](03-dates-as-data.md).  

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

### Tidied Data

You can download a cleaned version of the messy data [here](data/survey_data_spreadsheet_clean.xlsx) to see what a tidy version of this dataset looks like. Points to consider:

- Multiple tables have been combined into a single table where each observation has it's own row.
- Column headings (or variable names) have been simplified.
- The species-sex values from one of the 2014 tables have been broken up.
- Missing data is represented by blank cells.
- A `calibrated` column has been added to remove the need for messy formatting.

This tidy dataset is an example of data in 'long format'. However, we tend to be more familiar with data in 'wide' format because that is often how people store data in spreadsheets. 

For example, say you have several subjects and you are measuring a variable each day for each subject. The data would look like this in wide format:

| subject | sex | region | day1 | day2 | day3 |
| ------- | --- | ------ | ---- | ---- | ---- |
| 001     | m   | nth    | 2.5  | 2.7  | 2.6  |
| 002     | f   | sth    | 3.1  | 5.2  | 4.3  |
| 003     | f   | wst    | 4.2  | 5.1  | 3.9  |

Data in wide format expands by adding more columns. If we continued taking a measurment from each subject for 3 more days we would add day4-day6 as columns to the right. 

Data in long format expands by adding additional rows below. The above data in long format would look like this:

| subject | sex | region | day | value |
| ------- | --- | ------ | --- | ----- |
| 001     | m   | nth    | 1   | 2.5   |
| 001     | m   | nth    | 2   | 2.7   |
| 001     | m   | nth    | 3   | 2.6   |
| 002     | f   | sth    | 1   | 3.1   |
| 002     | f   | sth    | 2   | 5.2   |
| 002     | f   | sth    | 3   | 4.3   |
| 003     | f   | wst    | 1   | 4.2   |
| 003     | f   | wst    | 2   | 5.1   |
| 003     | f   | wst    | 3   | 3.9   |

You can see how `day` has been added as it's own column, and each measurement has gone into the `value` column. Note also how `subject`, `sex`, and `region` are repeated to give each `day`/`value` combination their own row. This means long format data is often larger than wide format due to the repetition. 

Data in 'long' format is often much easier to do statsitics on and to visualise in plots, and this is especially the case with programming languages like R and Python. Therefore it is generally best to store data in long format so that you have maximum flexibility to subset the data any way you want. 

For example, we could see values for all females on day 2 by filtering out the other rows. But if our data was in wide format, we would need to filter out rows and columns. We'll learn how to switch between long and wide format data later in the R lesson.

:::::::::::::::::::::::::::::::::::::::: keypoints

- Never modify your raw data. Always make a copy before making any changes.
- Keep track of all of the steps you take to clean your data in a plain text file.
- Organize your data according to tidy data principles.
- Store your data in long format for maximum freedom when manipulating it later.

::::::::::::::::::::::::::::::::::::::::::::::::::
