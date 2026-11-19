# Zomato Restaurants Global Analysis Dashboard 🍽️

## About This Project 📌
This is my **first complete data analytics project** built using **Microsoft Excel** and **Power BI**. 

I took a raw dataset of **9,551 Zomato restaurant listings** across different countries and turned it into an interactive two-page dashboard. The goal was to make it easy for anyone to explore where restaurants are located globally, which brands are the most popular, how affordable they are and what services (like online delivery or table booking) each branch actually offers.

---

## What Results & Insights I Found 🔍
By analyzing the data and building the visuals here are the main takeaways I discovered:

* **Most Restaurants Are Budget-Friendly:** Almost **79% of all listings** fall into the Budget (**46.52%**) or Moderate (**32.55%**) price categories showing that everyday affordable dining makes up the vast majority of listings.
* **Heavy Concentration in India & Major Cities:** While Zomato has listings across the US, UAE, UK, Indonesia and South Africa the highest concentration of restaurants and customer votes comes from major Indian metro cities like New Delhi, Kolkata, Bangalore, Hyderabad and Mumbai.
* **Top-Voted Restaurant Chains:** Brands like **Barbeque Nation**, **AB's - Absolute Barbecues**, **Toit**, **Big Chill** and **Farzi Cafe** lead the platform in total customer votes.
* **Services Differ by Branch Not Just by Brand:** Even within the same restaurant chain services are not identical across every location. For example **Barbeque Nation** has outlets across multiple cities yet only its Dubai branch offers Table Booking while **Truffles** offers Online Delivery across both of its branches in Bangalore and Gurgaon.

---

## How I Built It (Step-by-Step) 🛠️

### 1. Cleaning the Data in Excel & Power Query
Real-world data is messy so before making any charts I cleaned the dataset:
* **Fixed Messy Text:** Cleaned up broken characters in restaurant names and addresses and removed extra hidden spaces so names and cities grouped properly.
* **Created Clearer Columns:** Calculated the **Average Cost for One Person** from the original cost-for-two column and grouped numeric price codes (`1` to `4`) into simple labels (`Budget`, `Moderate`, `Expensive`, `Luxury` and `Unknown`).
* **Split Multi-Cuisine Lists:** Originally a single cell listed multiple cuisines together (like *"North Indian, Chinese, Mughlai"*). I split and organized these into a separate cuisines table so users can filter by a single cuisine without messing up the numbers.

### 2. Organizing the Data Model (Star Schema)
Instead of keeping everything in one giant table I connected my main restaurant table (`restaurant_flat`) to two smaller lookup tables (`country_dim` and `cuisines_dim`). This kept the dashboard fast and ensured that clicking a country or cuisine filter updated every chart accurately.

### 3. Designing the Two-Page Interactive Dashboard
* **Page 1 — Executive Overview:** Gives the big picture with filters for **Country**, **Restaurant** and **Cuisines** alongside a top-voted bar chart, a global map, a pricing donut chart and a searchable restaurant directory with color-coded rating badges (`Excellent`, `Very Good`, `Good`, `Average`).
* **Page 2 — Outlet Drill-Through Profile:** Lets you right-click any restaurant on Page 1 to jump into a dedicated profile page for that brand. It shows four summary cards counting how many branches offer **Online Delivery**, **Table Booking**, **Instant Delivery** and **Order Menu Switching** followed by a full branch-by-branch address and rating table.

---

## What I Learned From This Project 💡
* **Clean Data Matters Most:** I learned that spending time cleaning messy text and splitting multi-value columns (like cuisines) in Excel and Power Query saves hours of headaches later in Power BI.
* **How Filters Behave Across Pages:** While building the drill-through page I ran into a tricky challenge where KPI cards were showing `"No"` or miscounting multi-branch restaurants because default card settings only looked at the first branch alphabetically. Learning how to use **Count** aggregations with **Visual-Level Filters (`is Yes`)** taught me how Power BI filters work under the hood.
* **Designing for the User:** Choosing a clean dark theme, adding color-coded rating badges and including simple **Back** and **Home** navigation buttons makes a dashboard much easier to read and explore.

---

## How I Used Generative AI 🤝
Since this was my **first hands-on project** I used **Generative AI as a learning and troubleshooting guide** along the way—mainly when I got stuck debugging why drill-through KPI cards weren't counting multi-branch restaurants properly or when writing DAX color-formatting rules. All the data cleaning, data modeling, visual design and testing were built and put together by me.

---

## How to View the Dashboard 🚀
1. Download the `.pbix` file from this repository.
2. Open it in **Microsoft Power BI Desktop**.
3. Use the dropdown filters at the top of **Page 1** to explore by Country, Restaurant or Cuisine.
4. **Right-click** any restaurant name in the chart or table $\rightarrow$ select **Drill through** $\rightarrow$ **Restaurants Drill Through** to see its individual branches and service counts.
