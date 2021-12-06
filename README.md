# Education Economic Factors In Different Countries

Group 1: [Adam Holsinger](https://github.com/AdamH18), [Adrianne Gelbach](https://github.com/adriannebunn), [Elo Ekor](https://github.com/eloekor), [Jackie Kim](https://github.com/kims32), [Kyuseok Nam](https://github.com/Kyuseok-nam), [Lauren Lui](https://github.com/laurenlui), [Shardul Joshi](https://github.com/joshardul)  
RPI Data Science - Fall 2021  
Professor Munasinghe

<br>

## Table of Contents
1. [Abstract](#abstract)
2. [Data management](#data-management)
    <ol type="a">
        <li><a href="#logical-collections">Logical collections</a></li>
        <li><a href="#physical-data-handling">Physical data handling</a></li>
        <li><a href="#security">Security</a></li>
        <li><a href="#interoperability-support">Interoperability support</a></li>
        <li><a href="#data-ownership">Data ownership</a></li>
        <li><a href="#metadata">Metadata</a></li>
        <li><a href="#persistence">Persistence</a></li>
        <li><a href="#discovery">Discovery</a></li>
        <li><a href="#dissemination">Dissemination</a></li>
    </ol>
3. [Conclusions](#conclusions)
4. [References](#references)

<br>

## Abstract
The UN department of Economic and Social Affairs Sustainable Development has outlined 17 goals for sustainable development. (THE 17 GOALS | Sustainable Development, n.d.)  Each goal has been addressed by the UNESCO Institute for Statistics in a project called, “Data for Sustainable Development Goals.” (UNESCO UIS, n.d.) We decided to approach Goal 4: “ensure inclusive and equitable quality education and promote lifelong learning opportunities for all.”  These goals are further divided into subgoals, and our plan is to study the Sustainable Development Goal 4.4, which targets “increas[ing] the number of youth and adults who have relevant skills, including technical and vocational skills, for employment, decent jobs and entrepreneurship.” The indicator used for this goal is: “identifying the proportion of youth and adults with information and communications technology skills, by type of skill.” (Goal 4 | Department of Economic and Social Affairs, n.d.) Addressing this target and goal begins with identifying education indicators in developing nations and improving it based on the education indicators in countries with low unemployment and higher mean wages.

The datasets we chose included reports from the UN (United Nations), UNESCO (United Nations Educational, Scientific and Cultural Organization), World Bank, OECD (Organization for Economic Co-Operation and Development), GESIS (GESIS – Leibniz Institute for the Social Sciences), ILO (International Labor Organization), and the CGDEV (Center for Global Development). We chose datasets from these organizations for several reasons. First, these are very reputable organizations that have compiled incredible data repositories that can provide information on the metrics we chose to analyze. Next, they allow us to compare countries throughout the world.

All formal project references (APA-style) can be found in the [references](#references) section at the end of the report.

<br>

## Data management

| [Logical collections](#logical-collections) | [Physical data handling](#physical-data-handling) | [Security](#security) | [Interoperability support](#interoperability-support) | [Data ownership](#data-ownership) | [Metadata](#metadata) | [Persistence](#persistence) | [Discovery](#discovery) | [Dissemination](#dissemination) |

### Logical collections
Our logical collections of raw data were represented in a straightforward directory structure, created as we downloaded them from our sources. Folders described the type of data that would be found in that directory. The following is the tree for the raw data.
```
data
├── economic
│   ├── AvgIncome
│   │   ├── GNI
│   │   │   ├── API_NY.GNP.PCAP.CD_DS2_en_csv_v2_3159868.csv
│   │   │   ├── Metadata_Country_API_NY.GNP.PCAP.CD_DS2_en_csv_v2_3159868.csv
│   │   │   └── Metadata_Indicator_API_NY.GNP.PCAP.CD_DS2_en_csv_v2_3159868.csv
│   │   ├── Median
│   │   │   └── country-median-data-2011-PPP-Diofasi-Birdsall.csv
│   │   └── UNdata_Export_20211112_234256215.csv
│   ├── ChildLabor
│   │   └── UNChildLabor.csv
│   ├── FoodDeficits
│   │   ├── 3YearAvg.csv
│   │   └── AnnualUnnourished.csv
│   ├── GDP
│   │   ├── Metadata_Country_API_NY.GDP.MKTP.CD_DS2_en_csv_v2_3263806.csv
│   │   ├── Metadata_Indicator_API_NY.GDP.MKTP.CD_DS2_en_csv_v2_3263806.csv
│   │   └── gdp_current.csv
│   ├── LaborStats
│   │   └── labor_statistics_un.csv
│   ├── Population
│   │   └── data.csv
│   └── UnemploymentRate
│       └── UNE_2EAP_SEX_AGE_RT_A-full-2021-11-12.csv
├── education
│   ├── attendance
│   │   ├── compulsory_duration.csv
│   │   └── early_education_rates.csv
│   ├── enrollment
│   │   ├── primary.csv
│   │   ├── secondary.csv
│   │   └── tertiary.csv
│   ├── literacy
│   │   └── 15+.csv
│   ├── school_life_expectancy
│   │   ├── drop_out_rates
│   │   │   ├── primary.csv
│   │   │   ├── primary_completion.csv
│   │   │   └── primary_to_secondary_transition.csv
│   │   ├── expectancy.csv
│   │   └── repeaters
│   │       ├── lower_secondary_counts.csv
│   │       ├── primary_counts.csv
│   │       └── primary_percentages.csv
│   └── teacher_student_ratio
│       ├── lower_secondary.csv
│       ├── primary.csv
│       └── upper_secondary.csv
├── education_spending
│   └── percentage_GDP.csv
└── synthesized_data.csv
```
After setting up this structure, we were able to synthesize the data (the process for which is described briefly in [physical data handling](#physical-data-handling)) and place the manipulated data into a single CSV file at the same level as the education, economic, and education_spending folders, as seen above.
### Physical data handling
The first interaction with the data was downloading our raw data from our various sources (UN, UNESCO, World Bank, OECD, GESIS, ILO, CGDEV) as CSV files and storing them all in the directory structure described above. From here, we could easily read these files into Python code using the Pandas package, and synthesize them into a single table to be stored as another CSV file in our data directory. This manipulation involved getting the most recent statistic for each feature for each country, and the eventual synthesized table had a row for each country and a column for each feature.

We stored this final table in the file [`synthesized_data_table.csv`](https://github.com/ITWSDataScience/EducationEconomicFactorsInDifferentCountriesGroup1Fall2021/blob/main/data/synthesized_data.csv), which is at the same level as the `education`, `economic`, and `education_spending` folders, so it could then be handed off to the members working on the analysis portion of the project.

For versioning, backups, archives, etc., we relied on Git, as all of our data and scripts were stored in this Github repository.
### Security
As mentioned above, all of our data and scripts were stored in this Github repository. This repository also provides our security measures. Writing/contributing to the repo was restricted to ourselves (the members of the group) and Dr. Munasinghe. However, it enables anyone on the Internet to view and download our data/scripts. 
### Interoperability support
From an interoperability standpoint, our data and scripts are very accessible by all. As previously mentioned, the repository can be viewed/downloaded by anyone on the Internet, all data is stored in CSV files, and our scripts are written in Python. All of these technologies are familiar to many people, and Github displays all of our files in a very readable format. For instance, it displays CSV files in a formatted table. Meanwhile, our scripts are written in Jupyter notebooks, which allow a user to write some Python code, display some output, and then continue writing code using the same live environment throughout the notebook. These are also displayed very nicely by Github.
### Data ownership
Data is publicly available and owned by the organizations that published the reports. The synthesized data is owned by our group, Dr. Munasinghe as our advisor on this project, and RPI as our institution.
### Metadata
For our metadata, we want to make sure that we provide information regarding the units of each data feature in our synthesized data, the original sources (organization, link) of the raw data that we used, and access/publish dates (in ISO 8601) for each original source. We stored all of this information in another CSV file called “metadata.csv,” and it is also displayed directly below this block. This table, combined with our data directory structure described in the [logical collections](#logical-collections) section of this plan, will provide provenance and necessary metadata for viewers of our project.
<!-- TODO: put metadata table here, link to metadata.csv in the blurb above -->
### Persistence
Just as was the case with [physical data handling](#physical-data-handling), [security](#security), and [interoperability support](#interoperability-support), our Github repository comes into play with the persistence portion of our data management plan as well. It will be accessible from here for the foreseeable future. We will also have presented to the rest of the class, so other students will be aware that they are able to view the data/scripts in the repo.
### Discovery
### Dissemination
These newly found correlations between education and employment were formatted into an easy-to-understand poster and PowerPoint presentation. The slide deck will be shared in the Data Science course at RPI on December 9th, 2021. Additionally, we will submit our poster to the ODSC East ([https://odsc.com/](https://odsc.com/)) conference to be held in Boston on April 19-23, 2022.

<br>

## Conclusions

<br>

## References

