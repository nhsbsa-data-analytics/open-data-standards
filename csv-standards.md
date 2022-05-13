# CSV standards

## 1. Introduction
All Open Data releases should be accompanied by a CSV file - or set of files - that contain the most granular data in a machine readable format. CSVs should be made available as additional resources if formatted summary tables are required for a release, these spreadsheets should follow the Government Statistical Service (GSS) guidance on [Releasing Statistics in Spreadsheets](https://analysisfunction.civilservice.gov.uk/policy-store/releasing-statistics-in-spreadsheets/) and be released in OpenDocument Spreadsheet format (.ODS).

These standards should be followed for all new Open Data releases with a view to migrate existing releases as part of business as usual publishing.

## 2. Standards
| No. | Standard |
| --- | --- |
| 1 | The file should be CSV format. CSV does not support MS Excel features such as multiple tabs, filters, formatting, or macros. These should all be removed from the file prior to saving as CSV if being produced manually. **It is recommended that automated processes be used to generate the CSV file, such as using a Reproducible Analytical Pipeline (RAP).** |
| 2 | The data should start in the top left of the file with a row of column headers. The file should only contain a single table of data, no notes, logos, or presentational whitespace should be included in the file. |
| 3 | Only the first row of data should contain column headers. These headers should be unique, comprised of alphanumeric characters only (no £, %, &, etc.), **not contain** any [SQL/ODBC reserved words](https://docs.microsoft.com/en-us/sql/odbc/reference/appendixes/reserved-keywords?view=sql-server-ver15), and be in snake case - both all upper and all lower case are acceptable (for example, `YEAR_MONTH`, `total_cost`). |
| 4 | Column headers should be in plain English and descriptive and consistently labeled across data sets (for example, `YEAR_MONTH` and `PRACTICE_NAME` **not** `MONTH` and `GP_SURGERY`). Abbreviations should be avoided where possible except for commonly understood terms (for example, `STP_NAME`, `NHS_REGION`), however all abbreviations should be described in the accompanying data dictionary. |
| 5 | All information should be contained within the data. Headers, titles, or filenames should not be the only source of information. Consider additional fields, such as date, to provide context. For example, a file named `england-dental-activity-march-2022.csv` should also have a date or month field, and possibly a country field also. |
| 6 | Make sure that commas and double quotes are successfully enclosed or escaped as necessary. |
| 7 | If the file is large (greater than 10MB) consider publishing an accompanying ZIP folder. If you file is very large (greater than 100MB) consider using reference and lookup tables. **ZIP folders should not replace your CSV file** |
| 8 | Keep the number individual CSV files to a minimum. If you require multiple summaries/views of the same data, publish the most granular data as a CSV file and provide an accompanying accessible spreadsheet with supporting summaries. |
| 9 | Maintain a consistent structure to your data between releases (same columns, datatypes, and format). Any changes, for example, adding a column, should be communicated to users ahead of time |
| 10 | Each column should only contain one datatype (`numeric`, `string`, `boolean`, etc.). Consider using an additional column to indicate Statistical Disclosure Control (SDC), missing values, and other data quality issues. The ['Using symbols and shorthand in tables'](https://analysisfunction.civilservice.gov.uk/policy-store/symbols-in-tables-definitions-and-help/) guidance from GSS should be followed. |
| 11 | Create and maintain good field level metadata via a data dictionary. |

## 3. Checklist

- [ ] is the file .csv format?
- [ ] does the data start in the top left of the file?
- [ ] is the first row a header row?
- [ ] are there any notes/logos/blank rows or columns in the file?
- [ ] are the column headers appropriately labeled and in `snake_case`?
- [ ] do any of these columns appear in other data sets? Are they consistently named?
- [ ] does the data contain all of the columns it needs to? Does the user know the time period of the data without having to find other context?
- [ ] do any of the fields contain commas or double quotes, such as an organisation name? Have these fields been escaped or enclosed correctly?
- [ ] how big is the file? Does it need to be compressed to allow quick downloading? Could organisation or other reference tables be used?
- [ ] how many CSV files are there? Could they be combined into a single file? Do you need supporting summary tables in a spreadsheet?
- [ ] is the structure and format of the data the same as before? Have users been informed if a column has been added/removed?
- [ ] are the datatypes in each column consistent?
- [ ] have you used additional columns to signify missing values, SDC, and other data quality issues?
- [ ] have you created a data dictionary? Does it need reviewing and updating for this release?
