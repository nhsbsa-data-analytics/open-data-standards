# NHS Business Services Authority - Open Data Standards

* [CSV standards](https://github.com/nhsbsa-data-analytics/open-data-standards/blob/main/csv-standards.md)
* [Data standards](https://github.com/nhsbsa-data-analytics/open-data-standards/blob/main/data-standards.md)

## 1. Context

### 1.1. Introduction
The NHSBSA is working with other public bodies in the Health and Social Care sector to align the ways in which we publish our Open Data. This cross-system group have established a set of Open Data Standards that you can see in draft on [NHS Digital's GitHub](https://github.com/NHSDigital/open-data-standards).

We have adopted these standards and extended them to meet our own publishing requirements. We are committed to publishing Open Data to a [3 star standard](http://5stardata.info/en/) and will seek user's views about meeting further standards.

This repository is intended to be used as guidance for all NHSBSA teams who wish to publish Open Data - whether this be on the NHSBSA website, or the [NHSBSA Open Data Portal (ODP)](https://opendata.nhsbsa.net/).

These standards should be adhered to as closely as possible for any new Open Data releases or when redesigning existing releases. They are compiled from recognised sources of best practice including:

* Office for National Statistics (ONS)
* NHS Digital
* Public Health Scotland (PHS)
* The Government Statistical Service (GSS)
* The Open Data Institute

### 1.2. Spreadsheets
This guidance is aimed primarily at CSV outputs. If you need to publish your data in a spreadsheet due to the need for multiple summaries in different tabs an accompanying CSV with the most granular data should be released alongiside it.

If publishing a spreadsheet, the [GSS guidance on Releasing Statistics in Spreadsheets](https://analysisfunction.civilservice.gov.uk/policy-store/releasing-statistics-in-spreadsheets/) should be followed to make the output as accessible as possible.

### 1.3. What is Open Data?
Open Data is data that is available to everyone, including the public, to access, use, and share in anyway they like. It allows:

* accountability - public sector bodies can be held to account on the issues that matter and the use of public funds and services can be scrutinised
* efficiency - publishing data can help identify duplication, waste, and other systemic issues that can be reviewed and addressed
* innovation - releasing data can help drive innovation across the Health and Social Care landscape and can be combined with other Open Data sets to form the basis of new products and services elsewhere

Open Data is not the same as data sharing. Sensitive and Personally Identifiable Information (PII) still requires the relevant governance in place before it can be shared with another organisation. Open Data is released under the [Open Government License](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/).

### 1.4. Do we have to release Open Data?
Since the release of the 2012 white paper - ['Open Data: unleashing the potential'](https://www.gov.uk/government/publications/open-data-white-paper-unleashing-the-potential) - the UK government has pursued a policy of 'Open by Default' for all public sector organisations. This was reinforced with the release of the [National Data Strategy](https://www.gov.uk/government/publications/uk-national-data-strategy/national-data-strategy) looking to make better use of data throughout the public sector including making more data Open.

## 2. Requirements
For each Open Data release there are a number of components that are required in order to be able to be published.

### 2.1. Data file
For all releases a machine readable CSV formatted according to these standards is required.

### 2.2. Data dictionary
The data dictionary defines and explains the columns present in the data set. These definitions should be taken from existing business definitions where possible and may already be defined in the central Data Dictionary tool. If you have defined a new field consider adding this to the central Data Dictionary tool to allow reuse in the future.

### 2.3. Supporting information/methodology document
A guidance document to accompany the data should be created to support the release. This should include information on:

* background information including how and why the data is captured and compiled - for example, is it from a digital app, workforce system, or other?
* any methodologies used to create measures in the data or join it to other sources - for example, have averages been calculated or measures using a denominator? Has external data such as ONS geography data been used?
* the strengths and limitations of the data - what can or can't the data be used for? Is it complete? Is it representative?
* an assessment of the quality of the data based on
    1. relevance
    2. accuracy and reliability
    3. timeliness and punctuality
    4. accessibility
    5. coherence and comparability
* a change log for when methodology or structure changes occur in the data
* how to contact the relevant team about the data and how to provide feedback

## 3. Contact us
If you have any questions or feedback about these standards, including ideas on how to improve them, you can contact us by:

* [opening an issue in this repository]()
* [visiting our Open Data Roadmap Discussions page](https://github.com/nhsbsa-data-analytics/open-data-roadmap/discussions)
* or email us at dataandinsightsupport@nhsbsa.nhs.uk 