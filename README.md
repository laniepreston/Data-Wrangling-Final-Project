# Data-Wrangling-Final-Project
Lanie Preston &amp; Floor Kouwenberg 

## Research Question
Did the ratio of Republicans to Democrats in the United States Congress influence per capita dairy production
between the years 1998-2018, given that Republicans more often receive lobbies from the dairy industry and send
subsidies to the dairy industry, than Democrats 1 ?

## Data Sources
We used the table of the party divisions from the United States Congress from Wikipedia’s page:
https://en.wikipedia.org/wiki/Party_divisions_of_United_States_Congresses#Party_divisions_by_Congress
To verify Wikipedia’s numbers, we cross-checked them against the official divisions listed on the government
website for the House of Representatives and the Senate:
Party Divisions in the House: https://history.house.gov/Institution/Party-Divisions/Party-Divisions/
Party Divisions in the Senate: https://www.senate.gov/history/partydiv.htm
Data from annual dairy production and farm subsidies program was accessed from the United States Department
of Agriculture (USDA) database: https://www.ers.usda.gov/data-products/dairy-data.aspx
The amount of lobbies awarded from the dairy industry to politicians, as well as the party affiliation of those
politicians receiving lobbies, was found on the website for the Center for Responsive Politics:
Annual lobbies: https://www.opensecrets.org/federal-lobbying/industries/summary?id=a04&amp;cycle=2019
Party split of dairy lobby recipients: https://www.opensecrets.org/industries/indus.php?ind=a04


## Data Wrangling Methods
We employed several data wrangling methods to complete this project. Data on the party divisions within the US
Congress was the most difficult to “wrangle”. We read in HTML from the Wikipedia page on party divisions over
the years (we cross-referenced these numbers with sources from official United States congress websites; the
Wikipedia table just had a more convenient format). We employed several clean-up techniques for this
DataFrame, including dropping a number of columns and rows that were not relevant to our research, renaming
certain columns, and converting string values to integer values to make them easier to work with. Finally, we
created a new, per-year data frame using iterrows and a for loop to ensure a DataFrame that was readable and
compatible with other datasets. Data on the party divisions of dairy lobbies can be found here:
https://www.opensecrets.org/industries/indus.php?ind=a04


For extracting data on lobbying and subsidies, we read in CSV files that we downloaded from two sources, the
USDA and the Center for Responsive Politics. For the data on subsidies, we initially had to create 3 separate
DataFrames, as data was stored on the USDA website over a period of 10 years starting with 1990. To do so, we
deleted unnecessary columns and labels and reset indices so that we could merge said DataFrames. We then
isolated values relating to dairy and milk production using regular expressions and converted all dollar values from
string or float to int. We also handled missing values for subsidies by replacing missing data from before the dairy
protection subsidy programs were launched with zeros and replacing missing values and outliers in the lobbying
amounts with the mean of the preceding and following values.
Dairy production was the easiest table to handle in that it required simply reading in the CSV file obtained from the
USDA website, dropping the NaN values, and isolating the relevant column.
