# Zomato Restaurants Global Analysis Dashboard 🍽️

## About This Project 📌
This is my **first complete data analytics project** built using **Microsoft Excel** and **Power BI**. 
I took a raw dataset of **9,552 Zomato restaurant listings** across different countries and turned it into an interactive two-page dashboard. 

The goal was to make it easy for viewers to explore:
* **Where restaurants are located globally** using an interactive world map.
* **Which restaurant brands are the most popular** based on total customer votes and quality ratings.
* **How affordable dining options are** across Budget, Moderate, Expensive and Luxury price tiers.
* **Which restaurants and specific branches offer key services** using four dedicated KPI cards on the drill-through page to show exact branch counts for **Online Delivery**, **Table Booking**, **Instant Delivery** and **Order Menu Switching** alongside a full outlet-by-outlet breakdown.

---

## Exploratory Data Analysis (EDA) 🔎
Before building any charts I explored the raw dataset in Excel and Power Query to understand its structure and spot patterns or anomalies:
* **Checking Data Quality & Missing Values:** Inspected all 9,552 rows for blank entries, corrupted text encodings, hidden spaces and unmapped price ranges (`0` values categorized as `Unknown`).
* **Distribution & Outlier Review:** Checked the spread of customer votes, aggregate ratings and dining costs across countries to see which regions and restaurant chains dominated the dataset.
* **Service Flag Verification:** Examined how binary columns (`has_online_delivery`, `has_table_booking`, `is_delivering_now` and `switch_to_order_menu`) behaved across multi-branch chains versus single-outlet restaurants.
* **Multi-Valued Column Inspection:** Identified that the `cuisines` column stored multiple comma-separated values per cell which guided my decision to normalize it into a separate lookup table.

---

## What Results & Insights I Found 🔍
By analyzing the data and building the visuals here are the main takeaways I discovered:

* **Most Restaurants Are Budget-Friendly:** Almost **79% of all listings** fall into the Budget (**46.52%**) or Moderate (**32.55%**) price categories showing that everyday affordable dining makes up the vast majority of listings.
* **Heavy Concentration in India & Major Cities:** While Zomato has listings across the US, UAE, UK, Indonesia and South Africa the highest concentration of restaurants and customer votes comes from major Indian metro cities like New Delhi, Kolkata, Bangalore, Hyderabad and Mumbai.
* **Top-Voted Restaurant Chains:** Brands like **Barbeque Nation**, **AB's Absolute Barbecues**, **Toit**, **Big Chill** and **Farzi Cafe** lead the platform in total customer votes.
* **Services Differ by Branch Not Just by Brand:** Even within the same restaurant chain services are not identical across every location. For example **Barbeque Nation** has outlets across multiple cities yet only its Dubai branch offers Table Booking while **Truffles** offers Online Delivery across both of its branches in Bangalore and Gurgaon.

---

## How I Built It (Step-by-Step) 🛠️

### 1. Data Cleaning & Preparation in Excel and Power Query
* **Fixed Messy Text:** Cleaned broken characters in restaurant names and addresses and removed extra hidden spaces (`TRIM` and `CLEAN`) so names and cities grouped properly.
* **Created Clearer Columns:** Calculated **Average Cost for One Person** from the original cost for two column.
* **Split Multi-Cuisine Lists:** Separated cells containing multiple comma-separated cuisines (such as *"North Indian, Chinese, Mughlai"*) into individual rows in a dedicated `cuisines_dim` table so users can filter by a single cuisine without inflating vote counts.

### 2. Data Modeling & DAX Calculations in Power BI
* **Star Schema Data Model:** Connected the main restaurant table (`restaurant_flat`) to two smaller lookup tables (`country_dim` and `cuisines_dim`) so country and cuisine slicers filter all visuals accurately.
* **DAX Measures & Calculated Logic:**
  * **`Price_Tier`:** Grouped numeric price codes (`1` to `4`) into clear affordability labels (`Budget`, `Moderate`, `Expensive`, `Luxury` and `Unknown`).
  * **`Rating_Hex_Code`:** Assigned custom hex color codes to rating labels (`Excellent`, `Very Good`, `Good` and `Average`) for conditional color badges in tables.
  * **`Top_Rating_Rank`:** Calculated rating rank logic to sort and evaluate outlet quality across branches.
  * **Branch Service Counts:** Configured the four drill-through KPI cards using `Count` aggregations paired with visual-level filters (`is Yes`) to accurately count active branches for **Online Delivery**, **Table Booking**, **Instant Delivery** and **Order Menu Switching**.

### 3. Designing the Two-Page Interactive Dashboard
* **Page 1 (Executive Overview):** Displays dropdown slicers for **Country**, **Restaurant** and **Cuisines** alongside a top-voted restaurant bar chart, a global map, a pricing donut chart and a searchable restaurant directory with color-coded rating badges.
* **Page 2 (Outlet Drill-Through Profile):** Lets users right-click any restaurant on Page 1 (or use the drill-through button) to open a brand profile page featuring four service availability KPI cards, a full branch-by-branch address and rating table and custom **Home** and **Back** navigation buttons.

---

## Charts & Visuals Used (And Why) 📊

### Page 1: Executive Overview
* **Horizontal Bar Chart (Most Popular Dining Spots):** Used because horizontal bars keep long restaurant names readable without cutting off text while clearly ranking the top 10 most-voted brands.
* **Global Map (Global Restaurant Density & Presence):** Used to plot exact latitude and longitude coordinates so viewers can visually spot restaurant concentration across countries and cities.
* **Donut Chart (Dining Affordability & Price Tiers):** Used to fit a compact layout while clearly showing the percentage share of Budget, Moderate, Expensive and Luxury listings at a glance.
* **Directory Table (Restaurant Directory & Quality Ratings):** Used to display granular text details like city, locality, cuisines and color-coded rating badges while letting users right-click any row to drill through.
* **Dropdown Slicers (Country, Restaurant and Cuisines):** Used to save screen space while letting users filter the entire page interactively.

### Page 2: Outlet Drill-Through Profile
* **Four KPI Cards (Service Availability Counts):** Used to highlight the exact number of branches offering Online Delivery, Table Booking, Instant Delivery and Order Menu Switching at a quick glance.
* **Branch Breakdown Table (Outlet Directory & Ratings Breakdown):** Used alongside the KPI cards to list every individual branch location, address, cost for one person, rating badge and specific Yes or No service status.

---

## What I Learned From This Project 💡
* **Clean Data Matters Most:** Spending time cleaning messy text and splitting multi-value columns (like cuisines) in Excel and Power Query saves hours of headaches later in Power BI.
* **How Filters Behave Across Pages:** While building the drill-through page I ran into a challenge where KPI cards showed `"No"` or miscounted multi-branch restaurants because default card settings only checked the first branch alphabetically. Using `Count` aggregations with visual-level filters (`is Yes`) taught me how Power BI filter context works under the hood.
* **Designing for the User:** Choosing a clean dark theme, adding color-coded rating badges and placing clear **Home** and **Back** navigation buttons makes a dashboard much easier to read and explore.

---

## How I Used Generative AI 🤝
Since this was my first hands-on project I used **Generative AI as a learning and troubleshooting guide** along the way, mainly when debugging why drill-through KPI cards were not counting multi-branch restaurants properly or when writing DAX color-formatting rules. All data exploration, data cleaning, data modeling, visual design and testing were built and put together by me.

---

## Files in This Repository 📂
* `Zomato_Analysis_Dashboard.pbix`: The complete interactive Power BI report.
* `zomato_restaurants_dataset.xlsx`: The Excel workbook containing both the raw and cleaned Zomato datasets.
* `README.md`: Project summary and documentation.

---

## How to View the Dashboard 🚀
1. Download the `.pbix` file from this repository.
2. Open it in **Microsoft Power BI Desktop**.
3. Use the dropdown filters at the top of **Page 1** to explore by Country, Restaurant or Cuisine.
4. **Right-click** any restaurant name in the chart or table $\rightarrow$ select **Drill through** $\rightarrow$ **Restaurants Drill Through** to see its individual branches and service counts.
