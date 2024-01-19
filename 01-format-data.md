---
title: Formatting data tables in Spreadsheets
teaching: 15
exercises: 20
---

::::::::::::::::::::::::::::::::::::::: objectives

- Describe best practices for data entry and formatting in spreadsheets.
- Apply best practices to arrange variables and observations in a spreadsheet.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How do we properly format data in spreadsheets?

::::::::::::::::::::::::::::::::::::::::::::::::::

Spreadsheets are ubiquitous in research environments, yet many researchers are never taught how to properly format tabular data to ensure it is easy to analyse later.

Since most researchers use Excel as their primary spreadsheet program, the rest of this lesson will make use of examples using Excel. Free alternatives including LibreOffice Calc and Google Sheets can be used, but commands may differ between programs.

### What this lesson will not teach you

- How to do *statistics* in a spreadsheet
- How to do *plotting* in a spreadsheet
- How to *write code* in spreadsheet programs

## Problems with Spreadsheets

Spreadsheet programs like Excel were originally designed to enter, manipulate, and visualise financial data. It's easy to run into problems when working with research data when we forget Excel's purpose and limitations. For example:

- Be very cautious when opening and saving research data in Excel because by default it automatically reformats certain types of data, and this can introduce major errors (we'll explore an example 
later when we talk about dates).
- Making tables 'pretty' with merged cells, borders, highlighting, and notes in the margin mean that the data will not be recognised when imported into more specialised data analysis software,and will first require extensive clean up. 
- Statistics and figures generated within 'point and click' software like Excel cannot be replicated by someone else without detailed instructions, and it's easy to introduce errors when performing these kinds of actions by hand.

Doing statistics, plotting data, writing code, and doing in-depth data cleaning are best handled by other software which has been designed for these tasks. Data Carpentry includes lessons on Openrefine and R, which are better suited to performing these kinds of operations.

:::::::::::::::::::::::::::::::::::::::::  callout

## Exercise

- 
  

::::::::::::::::::::::::::::::::::::::::::::::::::

## Structuring Data in Spreadsheets

There are, however, useful things we can do with spreadsheet software to help us
with our research. In particular, quality control features can ensure that data
entered manually is standardised and free of errors. Ensuring tabular data is structured
in a way that computers understand means we can harness the power of programming languags like R or Python to perform complex analyses with a few lines of code. But to do that, we need to set up our data in a way the computer can understand (and computers are very
literal). 

The number one rule for working with tabular data in spreadsheet software is to keep it "tidy":

1. Put all your variables in columns - the thing you're measuring, like 'weight' or 'temperature'.
2. Put each observation in its own row.
3. Don't combine multiple pieces of information in one cell. You want maximum freedom to sort or subset your data later on.
4. Keep a copy of the raw data, untouched, in it's own folder.
5. Export the cleaned or modified data to a text-based format like CSV (comma-separated values) format. This ensures anyone can open the data, and is best-practise when depositing to research data repositories.

### Portal Project Teaching Dataset

The data used across the Data Carpentry lessons is a simplified version of the Portal Project Database designed for teaching. This dataset contains observations taken from a small mammal community in southern Arizona as part of a project studying the effects of rodents and ants on the plant community. The rodents are sampled on a series of 24 plots, with different experimental manipulations controlling which rodents are allowed to access which plots.

The study has been running for almost 40 years and the full dataset has been used in over 100 publications. The data we're going to look at has been simplified a little bit for the workshop, but the full version is available to download if you're interested.  


:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise

We're going to open up a messy version of a spreadsheet containing some of the Portal data. You can get a copy of the spreadsheet [here](https://ndownloader.figshare.com/files/2252083).

You can see that the data is spread across two tabs within this Excel workbook. Let's assume two field assistants conducted the surveys, one in 2013 and one in 2014, and they both kept track of the data in their own way in tabs `2013` and `2014` of the workbook. Let's say you were the person in charge of this project and you wanted to start analysing the data.

With the person next to you (if the workshop is in-person), or in the chat (if the workshop is online), identify what is wrong with this spreadsheet and what you could do to fix the problem. 

**Important** Do not forget to create a new file for the cleaned data. Never modify your original (raw) data.


:::::::::::::::  solution

## Solution

- All the mistakes in [02-common-mistakes](02-common-mistakes.md) are present in the messy dataset. As different points 
  are brought up, refer to [02-common-mistakes](02-common-mistakes.md) or expand a bit on the point.
- Note: There is a problem with dates in table 'plot 3' in the `2014` tab. The field assistant who collected the data
  for year 2014 initially forgot to include their data for 'plot 3'. They came back in 2015 to include the missing data and
  entered the dates for 'plot 3' in the dataset without the year. Excel automatically filled in the missing year as the
  current year (i.e. 2015) - introducing an error in the data without the field assistant realising. If you get a response
  from the participants that they've spotted and fixed the problem with date, you can say you'll come back to dates again
  towards the end of lesson in episode [03-dates-as-data](03-dates-as-data.md). If participants have not spotted the
  problem with dates in 'plot 3' table, that's fine as you will address peculiarities of working with dates in
  spreadsheets in episode [03-dates-as-data](03-dates-as-data.md).  
  

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::: keypoints

- Never modify your raw data. Always make a copy before making any changes.
- Keep track of all of the steps you take to clean your data in a plain text file.
- Organize your data according to tidy data principles.

::::::::::::::::::::::::::::::::::::::::::::::::::


