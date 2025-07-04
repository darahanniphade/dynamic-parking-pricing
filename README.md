# dynamic-parking-pricing
Summer Analytics 2025 Capstone Project – Dynamic pricing for urban parking lots using Pathway
# 🚗 Dynamic Pricing for Urban Parking Lots

> **Summer Analytics 2025 Capstone Project**  
> *Consulting & Analytics Club × Pathway*

---

## 🧠 Project Overview

This project implements a **real-time dynamic pricing system** for 14 urban parking lots. Using live demand signals such as occupancy, queue length, vehicle type, and nearby competition, we propose three interpretable pricing models.

Our solution runs in Google Colab using Pathway for streaming and Bokeh for visual dashboards.

---

## 🛠 Tech Stack

- 🐍 Python 3.12
- 📊 pandas, numpy
- 🔁 [Pathway](https://pathway.com/)
- 📈 Bokeh & Panel
- ☁️ Google Colab
- 💻 Git + GitHub

---

## 📁 Repository Structure

| File / Folder             | Description                                      |
|--------------------------|--------------------------------------------------|
| `dynamic_pricing.ipynb`  | Main Google Colab notebook with all 3 models     |
| `modified_dataset.csv`   | Provided real-time dataset                       |
| `model_1.png`            | Output graph – Avg Daily Parking Price           |
| `model_2.png`            | Output graph – Demand-Based Pricing              |
| `model_3.png`            | Output graph – Competitive Pricing               |
| `Dynamic_Pricing_Report.pdf` | *(Optional)* Written report                   |
| `README.md`              | This file                                        |

---

## 📈 Pricing Models Overview

### ✅ Model 1 – Baseline Pricing

- Based on fluctuation of occupancy within a day.
- Assumption: More variation = higher demand.

```python
price = 10 + (occ_max - occ_min) / capacity
price = base_price * (1 + λ * normalized_demand)
if avg_nearby < demand_price:
    price = max(avg_nearby - 1, 5)
else:
    price = min(demand_price + 0.5, 20)
flowchart LR
    A[CSV: modified_dataset.csv]
    B[Replay CSV Stream]
    C[Add Timestamp Columns]
    D[Tumbling Window Aggregates]
    E[Model Logic (1/2/3)]
    F[Bokeh Visual Output]

    A --> B --> C --> D --> E --> F

---

✅ **Next step:**  
After pasting this content into your `README.md`, click **“Commit changes”**.

Once you've uploaded your files and finished this, tell me — and I’ll do a final checklist review for submission!
Add complete README with model explanations and architecture
demand = a*(occupancy/capacity) + b*queue_length - c*traffic_level + d*is_special_day + e*vehicle_type_weight

price = base_price * (1 + λ * normalized_demand)
if avg_nearby < demand_price:
    price = max(avg_nearby - 1, 5)
else:
    price = min(demand_price + 0.5, 20)
flowchart LR
    A[CSV: modified_dataset.csv]
    B[Replay CSV Stream via Pathway]
    C[Add Timestamp Columns]
    D[Tumbling Window Aggregates (Daily)]
    E1[Model 1 Logic]
    E2[Model 2 Logic]
    E3[Model 3 Logic]
    F1[Bokeh Plot 1]
    F2[Bokeh Plot 2]
    F3[Bokeh Plot 3]

    A --> B --> C --> D --> E1 --> F1
                      D --> E2 --> F2
                      D --> E3 --> F3

---

### ✅ Next Step:
- Copy this entire block into your `README.md` on GitHub.
- Replace image links if you're renaming PNGs.
- Push your final `dynamic_pricing.ipynb`, dataset, and report if not done already.
- Let me know when it's uploaded, and I’ll verify everything for **final submission review**.
