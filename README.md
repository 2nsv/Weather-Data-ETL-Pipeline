# 🌦️ Weather Data ETL Pipeline

### Turning live weather data into structured, usable data.

This project is a small **end-to-end Data Engineering pipeline** built with Python.

Instead of working with a static dataset, the pipeline connects directly to the **OpenWeatherMap API**, collects live weather information from Egyptian cities, processes the raw responses, and stores the final structured data in **Azure SQL Server**.

---

## ⚡ The Pipeline

```text
        OpenWeatherMap
              │
              ▼
        ┌───────────┐
        │  EXTRACT  │
        │ API / JSON│
        └─────┬─────┘
              │
              ▼
        ┌───────────┐
        │ TRANSFORM │
        │   Pandas  │
        └─────┬─────┘
              │
              ▼
        ┌───────────┐
        │   LOAD    │
        │ Azure SQL │
        └───────────┘
```

The idea is simple:

**Get the data → make it reliable → put it somewhere useful.**

---

## 🧩 What Happens Inside?

### 01 — Extract

Weather data is requested through the OpenWeatherMap API for **10 cities across Egypt**, including Cairo, Alexandria, Port Said, Suez, Mansoura, Tanta, Luxor and Aswan.

The pipeline captures information such as:

`Temperature` · `Humidity` · `Pressure` · `Wind Speed` · `Coordinates` · `Weather Condition`

### 02 — Transform

Raw API responses aren't ready to be used directly.

Using **Pandas**, the data is cleaned and enriched by:

* Converting numerical values into proper data types
* Standardizing temperatures to Celsius
* Handling missing values
* Assigning geographical regions
* Classifying temperature as `Cold`, `Moderate`, or `Hot`
* Classifying humidity as `Low`, `Medium`, or `High`
* Adding an `IngestionTime`
* Validating the final dataset

### 03 — Load

Once the data is clean and validated, it is inserted into **Azure SQL Server** using **PyODBC**.

This creates a structured relational dataset that can later feed **SQL queries, dashboards, reports, or other data pipelines**.

---

## 🛠️ Built With

| Technology       | Purpose               |
| ---------------- | --------------------- |
| Python           | Pipeline development  |
| Requests         | API communication     |
| Pandas           | Data transformation   |
| PyODBC           | Database connectivity |
| OpenWeatherMap   | Data source           |
| Azure SQL Server | Data storage          |

---

## 🧠 Why This Project?

The goal wasn't just to call an API.

It was to practice the complete journey of data:

> **External Source → Raw Data → Clean Data → Enriched Data → Database**

This project focuses on the fundamentals of building a reliable **ETL workflow** and connecting different parts of a modern data pipeline together.

---

## 📂 Project

```text
Anas_Ahmed_Task/
├── weather_etl.ipynb
└── README.md
```

Open `weather_etl.ipynb` to explore the complete pipeline, transformations, and database loading process.

---

### 👨‍💻 Anas Ahmed

**Junior Data Engineer**
`Python` · `SQL` · `Databases` · `ETL`
