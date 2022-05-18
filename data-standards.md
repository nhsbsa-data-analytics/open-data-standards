# Data standards
By making sure that all of our Open Data release meet common standards we can make our data more coherent and easier to use. It will also reduce the burden on producer teams as resources, tools, and techniques can be re-used across data sets.

## 1. Tidy data
All Open Data must be in a ['Tidy' format](https://vita.had.co.nz/papers/tidy-data.pdf). This means:

* all variables are in their own column
* each observation must have its own row
* each value must have its own cell

This often means in practice creating 'longer' data sets as opposed to 'wide' ones. A common case for this is when time periods are used as column headers. For example:

| COUNTRY | 2019 | 2020 | 2021 |
| --- | --- | --- | --- |
| England | 11407 | 11487 | 11566 |

This data should be represented like below, with the `YEAR` variable given its own column along with the `NO_OF_PHARMACIES` variable:

| COUNTRY | YEAR | NO_OF_PHARMACIES |
| --- | --- | --- |
| England | 2019 | 11407 |
| England | 2020 | 11487 |
| England | 2021 | 11566 |

If you want to present your data in a horizontal way then it is advised to publish supporting summary tables with your Open Data CSV to facilitate this.

## 2. Dates
Dates are some of the most frustrating data items to work with for users. We can help ease these frustrations by using consistent formatting that makes the date both human and machine readable:

| Date type | Column name | Format | Structure |
| --- | --- | --- | --- |
| Full date | `DATE` | `YYYYMMDD` | This is the preferred format for full dates if the exact date is available in your data or the data is released at day level. For example, `20220101` |
| Year month | `YEAR_MONTH` | `YYYYMM` | This should be used for data that is available monthly instead of the format `MMM YY` - `Jan 22`. For example, `202201` |
| Calendar year | `YEAR` | `YYYY` | Should be used for data for full calendar years. For example, `2022` |
| Financial year | `FINANCIAL_YEAR` | `YYYY/YYYY` | Should be used for data for full financial years. For example, `2021/20222` |
| Calendar quarter | `CALENDAR_QUARTER` | `YYYY QN` | Should be used for quarterly data. For example, `2022 Q1` |
| Financial quarter | `FINANCIAL_QUARTER` | `YYYY/YYYY QN`|  Should be used for quarterly data. For example, `2021/2022 Q1` | 

## 3. Coding conventions
You should include standard codes in your data for variables that have them, for example:

* the BNF hierarchy
* organisations
* ONS geographies

This allows users to consistently map these variables across different time periods where their corresponding names may change. For example, the practice may change name over time, if only the practice name is included in the data then it is not clear to the user without a dedicated mapping document that 2 entries are related:

| YEAR MONTH | PRACTICE_NAME | ITEMS |
| --- | --- | --- |
| 202201 | PELAW MEDICAL PRACTICE | 23407 |
| 202202 | PELAW GENERAL MEDICAL PRACTICE | 18867 |

This small name change now makes it unclear that these 2 entries are for the same practice and make the data harder to work with. By using the associated `PRACTICE_CODE` it becomes clear.

| YEAR MONTH | PRACTICE_NAME | PRACTICE_CODE | ITEMS |
| --- | --- | --- | --- |
| 202201 | PELAW MEDICAL PRACTICE | A85611 | 23407 |
| 202202 | PELAW GENERAL MEDICAL PRACTICE | A85611 | 18867 |

If your data set is very large consider using reference tables and removing label fields from your data:

| YEAR_MONTH | PRACTICE_CODE | BNF_CODE | ITEMS |
| --- | --- | --- | --- |
| 202201 | A85611 | 0407010H0AAAMAM | 589 |
| 202201 | A86025 | 0212000B0AAABAB | 832 |

|PRACTICE_CODE | PRACTICE_NAME |
| --- | --- |
| A85611 | PELAW MEDICAL PRACTICE |
| A86025 | WESTERHOPE MEDICAL GROUP |

|BNF_CODE | BNF_NAME |
| --- | --- |
| 0407010H0AAAMAM | Paracetamol 500mg tablets |
| 0212000B0AAABAB | Atorvastatin 20mmg tablets |

Reference tables should be reused across data sets where possible.

# 4. Missing values
Where possible no missing values should be included in an Open Data release, if a value is 0 then it should be represented by a 0. Blank fields and cells when left unexplained risk confusion and misinterpretation. If a field does contain missing values then these need to be accompanied with an explanation in the associated metadata and guidance documentation. 

**Never use N/A** - NA is an ambiguous shorthand that can be interpreted as 'not available' or 'not applicable'. Including it within a column can also cause you to mix data types.

If a column has multiple reasons why a value might be missing then a separate qualifier column should be used following the GSS guidance for ['Using symbols and shorthand in tables'](https://analysisfunction.civilservice.gov.uk/policy-store/symbols-in-tables-definitions-and-help/). These qualifiers should not be used within the column itself, particularly if it is a numeric column to preserve its data type. Some of the most common qualifiers are:

| Symbol | Meaning |
| --- | --- |
| c | **Confidential -** The data point has been suppressed in line our Statistical Disclosure Control policy |
| f | **Forecast -** This data point is a calculated future value instead of an observed value |
| p | **Provisional -** This data point is yet to be finalised or expected to be revised |
| r | **Revised -** This data point has been revised since it was first published |
| x | **Not available -** This data point was not available. For example, data is not collected for a particular region |
| z | **Not applicable -** This data point is not applicable. For example, in NHS Jobs application data where people under the age of 16 cannot legally be employed, or in dispening contractor data where Dispensing Doctors cannot carry advanced services |

## 4.1. Examples

**Bad practice**
| QUESTION_NUMBER | AGE_GROUP | RESPONDENTS |
| --- | --- | --- |
| 1 | 16 to 20 |  |
| 1 | 21 to 25 | 32 |
| 1 | 26 to 30 | Suppressed |
| 2 | 16 to 20 | NA |
| 2 | 21 to 25 | 44 |
| 2 | 26 to 30 | 7 |

**Good practice**
| QUESTION_NUMBER | AGE_GROUP | RESPONDENTS | RESPONDENTS_QF |
| --- | --- | --- | --- |
| 1 | 16 to 20 |  | z |
| 1 | 21 to 25 | 32 |  |
| 1 | 26 to 30 |  | c |
| 2 | 16 to 20 |  | z |
| 2 | 21 to 25 | 44 |  |
| 2 | 26 to 30 | 7 |  |

# 5. Statistical disclosure control (SDC)
SDC is the process of making sure that the data we are releasing does not contain an personally identifiable data (PII) or cannot be used to discover anything about an individual. We have a separate SDC policy that should be followed for all Open Data releases

* [SDC policy](https://www.nhsbsa.nhs.uk/policies-and-procedures)