# data-512-homework_1
The goal of this project is to collect, analyze, and display monthly rare disease Wikipedia page view data from July 2015 through September 2024. This project also aims to follow best practices for scientific research and facilitating reproducibility. 

### About the Data
The source data is licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.en) and [GFDL](https://www.gnu.org/copyleft/fdl.html) according to the [Wikimedia Terms of Use](https://foundation.wikimedia.org/wiki/Policy:Terms_of_Use). Under the Wikimedia ToU, the data is available for use as long as users provide appropriate credit and follow the license requirements.

This project retrieves page view data from the Wikimedia API, [API reference here](https://doc.wikimedia.org/generated-data-platform/aqs/analytics-api/).
The project also uses [this CSV file](https://drive.google.com/file/d/15_FiKhBgXB2Ch9c0gAGYzKjF0DBhEPlY/view?usp=sharing) as an initial list of rare diseases to retrieve data for. This list references the database of rare diseases collected by [NORD](https://rarediseases.org).

### Output Files
The Jupyter Notebook outputs 3 data files (in JSON format) with a schema of article:time-series data. Article names are used as a key to a list of time-series data (in dictionary format). Each of these dictionaries contains a key-value pair for project, article, granularity, timestamp, agent, and views. Project, article, granularity, timestamp, and agent are of string types, and views is an integer. The timestamps are in YYYYMMDDHH format.

Schema:
| Column    | Data Type |
| -------- | ------- |
| Article Name | key (string) | 
| Time-series Data | item (list of dictionaries) |

Sample Data:
{"Klinefelter syndrome": [
            {
                "project": "en.wikipedia",
                "article": "Klinefelter_syndrome",
                "granularity": "monthly",
                "timestamp": "2015070100",
                "agent": "user",
                "views": 75311
            },
            {
                "project": "en.wikipedia",
                "article": "Klinefelter_syndrome",
                "granularity": "monthly",
                "timestamp": "2015080100",
                "agent": "user",
                "views": 68083
            }, ... ]}

File names:
rare-disease_monthly_cumulative_201507-202409.json
rare-disease_monthly_desktop_201507-202409.json
rare-disease_monthly_mobile_201507-202409.json

This project also outputs 3 graphs: Maximum Average and Minimum Average, Top 10 Peak Page Views, and Fewest Months of Data.
The Maximum Average and Minimum Average graph displays the view trends for the articles with the most and least average overall page views for each access type.
The Top 10 Peak Page Views graph displays the view trends for the top 10 articles with the most views at any given month for each access type.
The Fewest Months of Data graph displays the view trends for the 10 articles with the least amount of data for each access type, where least amount of data is defined by having the fewest months of data.

### Data Considerations
Though the intended range of data is from July 2015 through September 2024, there are articles with an incomplete set of data (we plot the most sparse 10 for each access type in the analysis).


