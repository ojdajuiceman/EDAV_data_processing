# EDAV_data_processing
Python script for processing data pulled from whitehouse.gov

### TLDR: 

Before analyzing this data visually in R, I wrote a script to clean and standardize all tables. This way, once I loaded them into R, they'd be easy to join with eachother and plot. The original tables (federal government spending data) are available on whitehouse.gov.

### Collection and cleaning pipeline

Upon inspecting the raw .xlsx files, it became clear that we were dealing exclusively with time-series data. Further, it was clear that all 57 files were in one of two formats, with a fairly evenly split between two types:

Type I -- Rows for year, columns for spending data.
Type II -- Columns for year, rows for spending data.

Our objective became to convert both of these file types into a single, standardized format. This would allow us to A) easily join datasets (using “year” as the join key) and B) transform and plot using ggplot2 as necessary.

In order to achieve this objective, we set up the following data processing pipeline:
1) Download .xlsx files, convert to CSV.
2) For Type I data, write a Python script to un-merge and systematically clean the column headers, saving back to CSV.
3) Import data into R by reading from CSVs
