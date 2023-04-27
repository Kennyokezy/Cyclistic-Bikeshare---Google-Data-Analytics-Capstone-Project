A full analysis on the Cyclistic Bikeshare Case Study of the Google Data Analytics Capstone Project using Excel

INTRODUCTION
This analysis is based on the Cyclistic bike-share case study recommended by Google for the completion of the Google Data Analytics Professional Certificate Course. Google recommends that each student completes a case study to showcase their understanding of each step of the data analysis process taught throughout the course, by making use of technical tools such as Excel, SQL, Tableau and R, in each stage to ultimately gather insights from large amounts of data. As such, I have completed my Capstone Project on the Cyclistic Case Study which involves a dataset from a fictional bike share company based in Chicago, USA. As I have learned from the Google Data Analytics program, I will follow the steps of the data analysis process: ask, prepare, process, analyze, share and act; in completing this project.
BACKGROUND
In this case study, I am assuming the position of a ‘junior data analyst’ working in the marketing analyst team at Cyclistic. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships and has assigned me the task of finding out how casual riders and annual members use Cyclistic bikes differently, in order to gain insights that could be used to design a new marketing strategy to convert casual riders into annual members.
ASK
The first step of any data analytics process involves gaining an in-depth understanding of the problem and the desired outcome. For this project, these were the answers I devised:
•	What is the problem we are trying to solve? Converting existing casual members into annual members
•	Why am I analysing this dataset? To understand how annual members and casual riders use Cyclistic bikes differently
•	Who are the stakeholders? Lily Moreno (Director of Marketing at Cyclistic), Cyclistic Marketing Team, Cyclistic Executive Team
•	How can my insights drive business decisions? To design marketing strategies aimed at converting casual riders into annual members
Prepare
The data used for this analysis was obtained from the original public dataset made available by Motivate International inc. a company employed by the City of Chicago to collect data on bike share usage. You can view the dataset by clicking here.
This data is current, reliable and without bias has it reflects the overall population Cyclistic bike users and has been stripped of all identifying information thereby ensuring privacy. There is not enough data to determine if casual riders are repeat-riders or if casual riders are residents of the Chicago area. The data is released under this license.
The most recent twelve months of data (January, 2022 – December, 2022) were used for this project. The data is organized in monthly csv files. The files are comprehensive for answering the business question and consist of 13 columns containing information related to ride id, rideable type, start time, end time, start location and end location and geographic coordinates, etc.
Our next step is making sure the data is stored appropriately and prepared for analysis. After downloading all 12 zip files and unzipping them, I housed the files in a temporary folder on my desktop. I also created subfolders for the .CSV files so that I have a copy of the original data.
PROCESS
For this project, I will be making use of Microsoft Excel. After opening each file, I did the following:
•	Checking column names across all the 12 original files
o	All 12 files had 13 columns with the same column names arranged in the same order.
•	Checking for missing values
o	Blanks were observed in the start and end_station_name columns which also reflected in their respective start and end_station_id columns. These records were removed from the data as they are bad data and could affect our overall analysis.
•	Checking of duplicate records.
o	There were no duplicate records for all 12 files.
•	Changing format of started_at and ended_at columns
o	Formatted as custom DATETIME (Format > Cells > Custom > yyyy-mm-dd h:mm:ss)
•	Creating a column called ride_length
o	Calculated the length of each ride by subtracting the column started_at from the column ended_at (example: =D2-C2)
o	Formatted as custom TIME (Format > Cells > Custom > [H]:MM:SS)
•	Creating a column called start_hour
o	Calculated the start hour of each ride using the started_at column with the hour function (example: =HOUR(C2))
o	Since this function gives us the hours in the 23-hour format, used the following IF function to create a new column that shows the time in the 12-hour format.
 
o	Then, in another column, I used the IF function to derive which hours were in the morning and which were for the afternoon:	 
o	Finally, I used the CONCATENATE function to combine the last two columns to derive my 12-hour time format for the start_hour	 
o	I copied the combine column and “Paste-Text_Only” in the column called start_hour and removed the other columns.
•	Creating a column called weekday
o	Calculated the day of the week that each ride started using the WEEKDAY function (example: =WEEKDAY(C2,1))
o	Then, converted the resultant numbers to their weekday names using the following
   and copied the resultant text into the column named weekday
•	Creating two new columns called month and season
o	Entered the month and season of each ride by auto-filling the month and season of each ride in each file 
•	Checking for other data anomalies:
o	Records with negative ride lengths or ride lengths equal to 0 were removed.
ANALYSIS
To analyse the whole data, I made use of Power Query, an Excel Add-in to transform and combine the 12 data files into one and added the combined data to the data model. As the maximum number of rows for Excel spreadsheets is rows, to make the data easier to analyse, I created 28 pivot tables in total using the following metrics:
•	Total Ride count vs Average ride length - calculated the total ride count and average ride length by rider type; used stacked column chart 
•	Total Ride Count - calculated the total ride count; vs rider type by rideable type; vs start hour by rider type; vs start hour by rideable type; vs start hour by weekday; vs weekday by rider type; vs weekday by rideable type; vs weekday by month; vs month by rider type; vs month by rideable type.
•	Sum of Ride Length - calculated the sum of ride length; vs rider type by rideable type; vs start hour by rider type; vs start hour by rideable type; vs start hour by weekday; vs weekday by rider type; vs weekday by rideable type; vs weekday by month; vs month by rider type; vs month by rideable type.
•	Average Ride Length - calculated the average ride length; vs rider type by rideable type; vs start hour by rider type; vs start hour by rideable type; vs start hour by weekday; vs weekday by rider type; vs weekday by rideable type; vs weekday by month; vs month by rider type; vs month by rideable type.
From these pivot tables, I created graphs to help visualize the data in order to get the best insights from the data.


![image](https://user-images.githubusercontent.com/106964101/234729362-a917e486-08e3-41e9-abec-4aeeb8e3973c.png)

Over the course of the year, annual members accounted for 59.5% of Cyclistic’s total rides while casual riders accounted for 40.5% of total rides. Also, as we can see in the above area chart, the average ride length of casual riders was double that of annual members (67% for casual riders compared to 33% for annual members).
Biker Habits
Monthly trends
Analysing the trends over the months, we notice a general increase in the total number of rides for both groups of riders from January to July where it peaks and then decreases for the rest of the year with members having the higher ride count month-on-month. A lot of activity is also seen around the summer months (June-August) which makes sense since bike riding is better suited for warmer weather conditions, (as seen in the major drop in total rides during the winter months (December-February)) which results in the higher ride lengths recorded in these seasons.
