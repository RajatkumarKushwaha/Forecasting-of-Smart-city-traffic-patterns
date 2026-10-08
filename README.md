# 🚦 Smart City Traffic Forecasting Dashboard

An end-to-end Machine Learning and Data Analytics project designed to predict and analyze traffic density patterns at major urban junctions. Built as part of the **IBM SkillsBuild Internship**, this project utilizes historical smart city traffic data to create a deployment-ready, interactive dashboard that assists city planning and traffic management authorities in making data-driven decisions.

---

## 🌟 Project Overview & Value

Urban traffic congestion is one of the biggest challenges in modern smart cities, leading to fuel wastage, increased pollution, and productivity losses. 

This project solves this problem by predicting the exact volume of vehicles at different junctions using time-series and environmental features. Instead of keeping the solution confined to a Jupyter Notebook code cell, it delivers an **Interactive Analytics Dashboard**. Traffic authorities can select any specific junction, date, or time to get live predictions along with deep data insights.

---

## 🛠️ Tech Stack & Key Libraries

- **Language:** Python 3.x
- **Machine Learning:** Scikit-Learn (`RandomForestRegressor`), Joblib
- **Data Manipulation:** Pandas, NumPy
- **Interactive UI (Dashboard):** IPyWidgets (`ipywidgets`)
- **Data Visualization:** Plotly Express (`plotly`)

---

## 📋 The Execution Plan (Step-by-Step Architecture)

The project follows a standard, rigorous data science lifecycle split into five core phases:

### Phase 1: Data Preprocessing & Feature Engineering
- **Datetime Parsing:** Converted raw timestamp strings into actionable datetime objects.
- **Feature Extraction:** Extracted multi-dimensional time features (`Year`, `Month`, `Day`, `Hour`, `DayOfWeek`) from a single timestamp to help the ML model catch seasonal, weekly, and peak-hour rhythms.
- **Data Formatting:** Cleaned unnecessary columns (`ID`, `DateTime`) after mapping to ensure the model receives clean, numeric arrays.

### Phase 2: Exploratory Data Analysis (EDA)
- **Junction Inferences:** Identified which junctions inherently carry the heaviest loads throughout the year.
- **Hourly Bottlenecks:** Plotted full-city traffic timelines to locate peak rush hours (e.g., office/school commute times).
- **Weekly Cycles:** Analyzed patterns across weekdays versus weekends to measure drop-offs or spikes in traffic density.

### Phase 3: Model Training & Validation
- **Train-Test Splitting:** Divided the data into an 80% training set and a 20% validation set using a locked `random_state` to ensure stable training evaluation.
- **Algorithm Choice:** Implemented a **Random Forest Regressor** due to its superior ability to handle non-linear time-series data and robustly prevent overfitting through ensemble decision trees.
- **Serialization:** Exported the trained weights into a compact `traffic_forecasting_model.pkl` file for backend integration.

### Phase 4: Frontend Dashboard Implementation
- Built a native UI inside Jupyter Notebook leveraging `ipywidgets`.
- Integrated a live drop-down menu for junctions, an explicit date picker, and a precise time input.
- Connected the UI trigger ("Predict Traffic") directly to the serialized model backend to compute vector-based matrix operations instantaneously.

### Phase 5: Dynamic Categorization & Status Mapping
- Wrapped the raw integer vehicle predictions into human-readable thresholds:
  - **🟢 Normal / Clear:** Below 15 vehicles/hour average.
  - **🟡 Moderate / Medium:** Between 15 and 35 vehicles/hour average.
  - **🔴 Heavy Traffic / Jam:** Above 35 vehicles/hour average.

---

## 📈 Model Performance Metrics

The Random Forest model yields exceptional predictive stability on completely unseen validation data:
- **Mean Absolute Error (MAE):** ~2.40 (On average, the model's prediction deviates by just ~2 gaadiyan from actual live counts).
- **Root Mean Squared Error (RMSE):** ~3.56
- **R-squared (R2) Score:** **0.9690 (~96.9% Variance Explained)** — indicating an extremely high level of real-world reliability suitable for enterprise applications.

---

## 🚀 Setup & How to Run the Dashboard

Follow these simple steps to run the interactive dashboard on your local machine:

### 1. Clone the Directory & Prepare Files
Ensure that all required project files are placed together in a **single workspace folder**:
```text
├── Traffic_Model.ipynb  (Your Main Notebook)
├── train_aWnotuB.csv      (Historical Dataset)
└── traffic_forecasting_model.pkl (Generated Model Pickled File)
```

### 2. Install Dependencies
Open your terminal, command prompt (CMD), or a Jupyter terminal cell, and run the following command to download the essential framework requirements:
```bash
pip install ipywidgets plotly pandas numpy joblib scikit-learn
```

### 3. Open and Execute the Pipeline
1. Launch Jupyter Notebook and open **`Traffic_Model.ipynb`**.
2. Click on the top menu bar: **Kernel -> Restart & Run All**.
3. Scroll to the very last cell of the notebook. You will see a beautiful interface containing input fields and a **Predict Traffic 🚦** button.

---

## 🔮 Future Enhancements
- **Web App Migration:** Porting the core framework over to a production-grade Streamlit or Flask server.
- **Weather API Integration:** Fetching live precipitation and visibility data to account for weather-induced road delays.
- **Multi-Junction Routing Optimizers:** Introducing pathfinding graphs (like Dijkstra's algorithm) to recommend alternative routes when a junction status turns **Red (🔴)**.

---
Developed with ❤️ for the IBM SkillsBuild Internship Program.
