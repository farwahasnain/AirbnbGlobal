# 🏠 Global Airbnb Performance Dashboard
### Power BI | Data Analytics | Travel & Hospitality

A multi-page interactive Power BI dashboard analyzing **279,712 Airbnb listings** across **10 major cities** worldwide, built using the [Maven Analytics Airbnb Dataset](https://mavenanalytics.io/data-playground/airbnb-listings-reviews).

---

## 📊 Dashboard Pages

### 1. Overview
![Overview Dashboard](https://github.com/farwahasnain/AirbnbGlobal/blob/main/overview.PNG)

A high-level snapshot of the global Airbnb market, tracking listing growth over time and platform lifecycle stages — from Introduction (pre-2010) through Growth, Maturity, Decline, Re-invention, and the impact of COVID-19.

**Key metrics:**
- 279,712 total listings across 10 cities
- 182K hosts and 5.37M reviews
- 144 unique property types
- Peak new listings reached in 2015, followed by a sharp COVID-19 driven decline post-2019

---

### 2. Hosting Growth
![Hosting Growth Dashboard](hosting_growth.PNG)

Explores the supply side of the Airbnb market — who is hosting, what they are offering, and how trustworthy the host base is.

**Key insights:**
- Entire place listings dominate at **65%** of all listings
- Only **18%** of hosts hold Superhost status, signaling a quality opportunity
- **41%** of listings are instantly bookable
- **72%** of hosts have verified identities
- Host growth peaked in **2015** and has declined since 2020 due to COVID-19

---

### 3. Customer Satisfaction
![Customer Satisfaction Dashboard](customer_satisfaction.PNG)

Examines demand-side performance through guest reviews, satisfaction scores, and city-level pricing patterns.

**Key insights:**
- Global average guest rating: **93.41 / 100**
- **Paris** and **Rome** lead in visitor volume (1.21M and 1.11M) at affordable avg prices ($113 and $105)
- **Mexico City** ranks highest in overall guest satisfaction at **94.84**
- **Hong Kong** scores lowest at **89.71**, indicating room for quality improvement
- **Cape Town** shows an anomalous avg price spike ($2,405) driven by luxury listing outliers

---

## 🗂️ Dataset

| Property | Details |
|---|---|
| Source | [Maven Analytics Data Playground](https://mavenanalytics.io/data-playground/airbnb-listings-reviews) |
| License | Public Domain |
| Tables | Listings, Reviews |
| Total listings | 279,712 |
| Total reviews | 5,373,000+ |
| Cities covered | Paris, Rome, New York, Sydney, Mexico City, Rio de Janeiro, Cape Town, Bangkok, Istanbul, Hong Kong |

---

## 💡 Business Questions Answered

1. How large is the Airbnb platform globally in terms of listings, hosts, cities, property types and reviews?
2. How did new listings grow over time from 2008 to 2022 — and what were the key lifecycle phases (Introduction, Growth, Maturity, Decline, Re-invention, COVID-19)?
3. When did Airbnb reach its peak supply, and what caused the decline?
4. How did each room type (Entire place, Private room, Hotel room, Shared room) contribute to listing growth over the years?
5. What was the impact of COVID-19 on the platform's listing volume?
6. How many total listings and hosts exist across the platform?
7. What proportion of hosts have achieved Superhost status — and what does that mean for quality?
8. What share of listings are instantly bookable, and how does that affect guest convenience?
9. How trustworthy is the host base — what percentage have verified identities?
10. How has the count of hosts grown and declined year over year?
11. What room types make up the listing supply, and which dominates?
12. What is the overall average guest rating across the entire platform?
13. Which cities attract the most visitors, and at what average nightly price?
14. Is there a relationship between visitor volume and pricing — do popular cities tend to be cheaper or more expensive?
15. Which property type is most popular among guests — Entire place or Entire apartment?
16. How do cities compare across specific satisfaction dimensions — Accuracy, Check-in, Cleanliness, Communication, Location and Value?
17. Which city has the highest overall guest satisfaction, and which has the lowest?
18. How do accuracy and cleanliness scores compare globally as standalone KPIs?

Across all three dashboards together, the report answers the single overarching business question:

**"How healthy is the global Airbnb marketplace — from supply growth and host quality, to guest demand and satisfaction — and which cities lead or lag across each dimension?"**

---

## 🧮 Key DAX Measures

```dax
-- Average Price = AVERAGE(Listings[price])
-- Total Listings = COUNT(Listings[listing_id])

-- Visitors (proxy)
Total Visitors = COUNTROWS('Reviews')

-- Average Rating (scaled to 100)
Average Rating = AVERAGE('Listings'[review_scores_rating])

-- Entire place = 
CALCULATE(
    COUNT (Listings[listing_id]), 
    Listings[room_type] = "Entire place"
)

-- Private room = 
CALCULATE(
    COUNT (Listings[listing_id]), 
    Listings[room_type] = "Private room"
)

-- Hotel room = 
CALCULATE(
    COUNT (Listings[listing_id]), 
    Listings[room_type] = "Hotel room"
)

-- Shared room = 
CALCULATE(
    COUNT (Listings[listing_id]), 
    Listings[room_type] = "Shared room"
)

-- Year = YEAR(Listings[host_since])

-- Superhost %
Superhost % = 
DIVIDE(
    COUNTROWS(FILTER('Listings', 'Listings'[host_is_superhost] = "t")),
    COUNTROWS('Listings')
)
```


---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| Power BI Desktop | Dashboard development and DAX modeling |
| Power Query | Data cleaning and transformation |
| DAX | Calculated measures and columns |
| Maven Analytics | Dataset source |

---

## 📁 Repository Structure

```

│── overview.png
│── hosting_growth.png
│── customer_satisfaction.png
├── AirbnbDashboard_Farwah.pbix
└── README.md
```



---

## 📥 Download Dashboard

The `.pbix` file is too large for GitHub (195MB). Download it directly from Google Drive:

👉 [Download Airbnb_Dashboard.pbix from Google Drive](https://drive.google.com/drive/folders/1EvcL_hQCNV2oIoN-T2TIvMXx8YbDSVv0?usp=sharing)

---

## 🚀 How to Use

1. Download the dataset from [Maven Analytics](https://mavenanalytics.io/data-playground/airbnb-listings-reviews)
2. Clone this repository
3. Open `Airbnb_Dashboard.pbix` in Power BI Desktop
4. Refresh the data source and point it to your downloaded dataset files
5. Explore the three dashboard pages using the city slicer to filter by location

---

## 👤 **Author**: Farwah Hasnain
📧 Contact: [farwah.hasnain@gmail.com] | 🌐 [LinkedIn](https://www.linkedin.com/in/farwah-hasnain/)

---

*Data source: Inside Airbnb (Public Domain) via Maven Analytics*

