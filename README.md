# Real-Time-TikTok-Data-Pipeline-for-Content-Performance-Insights
This project is an end-to-end TikTok analytics system built to monitor and analyze content performance using automated data extraction and visual analytics. By integrating the ScrapTik API, Python, and Power BI, the system provides real-time, actionable insights into post performance, audience engagement, and content strategy optimization.

## Overview
In February 2025, I began consistently posting on TikTok to share my journey in data analytics and content creation. After months of experimentation, I decided to build a solution that would go beyond content creation to answer: "What’s working, and why?"

This led to the development of a fully automated pipeline that pulls data from TikTok, processes and stores it efficiently, and visualizes the results for strategic decision-making.

---

## Project Folder & Assets

- [`Insight Report.md`](https://github.com/Olowookere-Abidemi/Real-Time-TikTok-Data-Pipeline-for-Content-Performance-Insights/blob/main/Insight%20Report.md) –  Insight Report 
- [`POWERBI DAX CODE.txt`](https://github.com/Olowookere-Abidemi/Real-Time-TikTok-Data-Pipeline-for-Content-Performance-Insights/blob/main/POWERBI%20DAX%20CODE.txt) – Dashboard metrics logic  
- [`PYTHON SCRIPT.ipynb`](https://github.com/Olowookere-Abidemi/Real-Time-TikTok-Data-Pipeline-for-Content-Performance-Insights/blob/main/Python%20Script.ipynb)) – Data extraction code  
- [`DASHBOARD.jpg`](https://github.com/Olowookere-Abidemi/Real-Time-TikTok-Data-Pipeline-for-Content-Performance-Insights/blob/main/DASHBOARD.jpg) – Visual report image

---

## Technical Stack

| Tool         | Purpose                                          |
| ------------ | ------------------------------------------------ |
| Python       | API integration, data extraction, transformation |
| ScrapTik API | Secure access to TikTok post/profile data        |
| .env         | API key and user ID security management          |
| Pandas       | Data cleaning, processing, CSV export            |
| Power BI     | Visual reporting and dashboarding                |

---

## Data Workflow

### Step 1: User ID Lookup

* Uses ScrapTik's `/search-users` endpoint
* Retrieves TikTok `user_id` 

### Step 2: Post Data Retrieval

* Uses `/user-posts` endpoint with `user_id`
* Extracts:

  * Video ID
  * Likes, comments, shares, views
  * Description, hashtags
  * Duration, sound title, post date/time

### Step 3: Deduplication & Merging

* Compares new data against existing CSV
* Prevents duplication and updates metrics accordingly

### Step 4: Data Transformation

* Adds computed metrics such as:

  * Engagement Rate = (Likes + Comments + Shares) / Views
  * Duration Category: short, medium, long
  * Extracted hashtags and sound categories

### Step 5: Logging and Error Handling

* Logs any API or processing error into an external `.txt` log
* Ensures script stability during long-term automation

---

## Output

The processed dataset is saved in CSV format with the following structure:

| Column                  | Description                         |
| ----------------------- | ----------------------------------- |
| Post ID                 | Unique TikTok video identifier      |
| Description             | Post caption text                   |
| Likes, Shares, Comments | Engagement metrics                  |
| Views                   | View count per video                |
| Engagement Rate         | Custom performance indicator        |
| Sound Title             | Audio used in post                  |
| Region                  | Inferred region data (if available) |
| Date, Duration          | Timestamp and video length          |
| Hashtags                | Extracted from post captions        |

---

## Power BI Dashboard Features

The CSV file is connected to Power BI for rich visualization. Key insights include:

* Total Posts and Views (with MoM change)
* Engagement Over Time
* Best Performing Days and Hours
* Duration vs Engagement Scatter Plot

Power BI uses DAX formulas, slicers, conditional formatting, and drill-through capabilities to deliver actionable insights.

![TikTok Dashboard](https://github.com/Olowookere-Abidemi/Real-Time-TikTok-Data-Pipeline-for-Content-Performance-Insights/blob/main/DASHBOARD.jpg?raw=true)

---

## Performance Insights (February – July)

* April was the most successful month with 1.14M views and 2,130 avg. engagements per post
* Morning hours (6AM–8AM) and Sundays performed best in terms of engagement
* Short-form videos (<15s) accounted for the highest engagement-per-view ratio
* Post frequency alone did not drive growth; content quality and timing were the key factors

---

## Key Outcomes

* Automated TikTok post tracking with zero manual effort
* Insight generation that feeds back into content planning
* Demonstrated skills in API integration, automation, and visual analytics

---

## How to Use or Reproduce

1. Clone this repository
2. Set up your `.env` file with ScrapTik credentials and your TikTok `user_id`
3. Run the Python script to extract and transform TikTok data
4. Open the Power BI file and connect it to the output CSV
5. Explore and share insights

---

## License

This project is open for learning and non-commercial use. Please credit appropriately if reused.


