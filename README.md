# Comprehensive Traffic Data Scraper for the City of Vancouver

## Project Overview
This project consists of a comprehensive scraper designed to download intersection traffic movement count data, including date, weather, vehicle, pedestrian, and bicycle volumes during peak hours (AM, MD, and PM), from the City of Vancouver's website. The data spans from 1989 to 2022 and encompasses various report types (htm, xlsx, and pdf). This effort aimed to standardize the analysis across all reports, defining AM period from 6 AM to 9 AM, MD from 9 AM to 3 PM, and PM from 4 PM to 8 PM. The project was executed in accordance with the City of Vancouver's Open Data License.

The versatility of the scraper allows for easy modification, enabling researchers to tailor the data extraction process to meet the specific needs of their studies. Whether for predicting traffic patterns, analyzing pedestrian flows, or planning urban infrastructure, the data procured through this tool holds the potential to significantly advance our understanding of urban environments.

In essence, this scraper is more than just a coding project; it's a bridge between open data and the transformative insights machine learning can offer in the area of transportation engineering

### Case Study
The intersection_match_n_cluster.ipynb notebook demonstrates a focused analysis on matching the intersection names using `fuzzywuzzy`, geocoding them using a public API, and clustering the TMC counts using `DBSCAN`. Created with the intent to support open data initiatives and machine learning in urban planning, this notebook is shared publicly, encouraging the use of the prepared data to derive actionable insights for urban development and traffic management.

The exported data from this notebook is visualized via an interesting Tableau dashboard excluding a few poorly geo coded intersections. 

https://public.tableau.com/app/profile/erfan.hajibandeh/viz/CityOfVancouverTMCs1989-2022/MapReport?publish=yes

As a simple observation, I have analyzed traffic data from 2019 to identify intersections suitable for conversion into pedestrian-and-bike-only zones. Focusing on TMC counts with low vehicle volumes (bottom 20th percentile) and high pedestrian and bike activity (top 80th percentile), I have mapped the TMC counts that meet this criteria

![Active Transportation Intersections](data/viz/80_20_viz.png)

## Getting Started

### Prerequisites
- Python 3.10
- Pip for Python package installation

### Installation
1. Clone the repository to your local machine:
   ```sh
   git clone https://github.com/erfanhajibandeh/traffic-growh-prediction.git
   ```
2. Install the required Python packages:
   ```sh
   pip install -r requirements.txt
   ```
   
### Usage
To run the scraper, execute the `scrape.py` script from the command line:
```sh
python scrape.py
```
This script initiates the scraping process, downloading traffic count data and storing it in specified directories for both old (1989-2011) and recent (2011-2022) TMC counts using the following two raw spreadsheets that contain critical information for crafting the download links and scraping the data.

old_intersection-traffic-movement-counts.csv 
recent_intersection-traffic-movement-counts.csv

## Project Structure
- `scrape.py`: The main script that implements the scraping logic.
- `/data/raw`: Directory containing raw data files for old and recent TMC counts.
- `/data/scraped`: Directory where the processed data files are stored.

### WebScraper and TMCScraper Classes
The `scrape.py` script includes several classes:
- `WebScraper`: A base class for managing web scraping sessions.
- `OldTMCScraper`: Inherits from `WebScraper`, tailored for scraping old .htm TMC data (pre-2011).
- `RecentTMCScraper`: Inherits from `WebScraper`, designed for scraping recent .xlsx and .pdf TMC data (post-2011).

These classes manage the complexities of navigating and extracting data from the City of Vancouver's web pages, handling different data formats, and ensuring data is accurately captured for each time period.

## License
This project is licensed under the terms of the Open Government Licence - Vancouver. See the LICENSE file for more details.

## Acknowledgments
This project was made possible by the open data provided by the City of Vancouver. Special thanks to the City of Vancouver for supporting open data initiatives and to all contributors to this project.

For more information on the license under which this data is released, please visit: [City of Vancouver Open Data License](https://opendata.vancouver.ca/pages/licence/).

## Contact
For any questions or suggestions regarding this project, please contact Erfan Hajibandeh.