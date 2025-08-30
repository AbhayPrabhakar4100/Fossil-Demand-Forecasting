# fossil-demand-forecasting

## 📝 Project Background
Fossil is a global name in fashion retail, best known for its watches, handbags, and accessories. Like many retailers, Fossil faces two persistent challenges:  
- **Overproduction**, which drives up storage and holding costs  
- **Underproduction**, which results in missed sales and dissatisfied customers  

Because production cycles are long and customer demand is volatile, **accurate demand forecasting** is essential to balance inventory and ensure smooth operations.  
This project focuses on forecasting watch demand more precisely to support data-driven inventory and supply chain decisions.

---

## 📊 Dataset Summary
The dataset contains **44,907 records with 45 variables**, combining categorical and numerical information relevant to demand prediction.

### Key Categorical Variables
- **sku_name** → SKU identifier for each product  
- **month** → Calendar month of the record  
- **product_lifecycle_stage** → Position in product lifecycle (intro, growth, maturity, decline)  
- **cat_gender_both / men / women** → Target customer group  
- **disc_month** → Indicator if sales were below mean price (discount month)  
- **cum_disc** → Rolling effect of discounts over 3 months  
- **weeks** → Number of weekends in the month  

### Core Numerical Variables
- **starting_inventory** → Initial stock at the start of month  
- **sellin** → Demand placed by customers (target variable)  
- **sellin_channel_X** → Channel-level sell-in demand (1–8)  
- **sellout** → Final sales to end customers  
- **onhand_inventory** → Post-sales stock on customer side  
- **leftover_inventory** → Unsold stock after cycle  
- **sellout_channel_X** → Channel-level sell-out demand (1–10)  
- **onhand_inventory_channel_X** → Channel-wise remaining stock  
- **price** → Retail price of SKU  
- **year** → Year of record  
- **flag100** → Binary discount flag  

---

## 🔧 Approach & Methodology
1. **Data Cleaning**  
   - Removed anomalies such as negative target values  
   - Encoded categorical features using **Label Encoding** and **Word2Vec**  

2. **Feature Engineering**  
   - Added lead/lag features to capture demand history  
   - Incorporated ARIMA-based features from `sellout` to represent time trends  

3. **Model Development**  
   - Hyperparameters tuned with **Bayesian Optimization**  
   - Built a **Stacking Model** ensemble for robust performance  
   - Evaluated using **K-fold CV** with **MAPE** as the main metric  

---

## 🎯 Results
- Achieved **5% Mean Absolute Percentage Error (MAPE)**  
- Predictions closely align with actual demand, minimizing forecast error  

**Why it matters:**  
- 5% MAPE = highly reliable forecasts with very small deviation from reality  

---

## 📈 Business Impact
- **Inventory Efficiency** → Estimated **$400M savings** in carrying costs  
- **Revenue Protection** → Safeguards **$2.8B in net sales** by reducing stockouts  
- **Profit Growth** → Improves EPS by ~**$0.41** through better demand planning  

---

## ⚙️ Installation
Clone the repo:  
```bash
git clone https://github.com/yourusername/fossil-demand-forecasting.git
