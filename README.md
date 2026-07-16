# Practical_Application_11.1

Required Assignment 11.1: What Drives the Price of a Car?

Link to [https://github.com/Suraj-BH/Practical_Application_11.1/blob/main/prompt_II.ipynb]

## Findings

### Business Understanding
Used car dealerships operate in a highly competitive market with tight margins. To maximize profit, they must optimize trade-in appraisal offers and price lot inventory accurately. 

Reframed as a data task, this project resolves a **Supervised Continuous Regression** problem. We aim to construct an interpretable model that maps independent parameters (such as vehicle age, mileage, engine size, and fuel type) to a continuous dependent target variable (`price`).

### 2. Data Understanding & Quality Assessment
The initial dataset consisted of 426,880 entries across 18 features. A thorough missing-value analysis revealed several critical data integrity concerns:

* **High Null-Count Features:** The `size` feature had over 71.7% missing entries, making it unusable for predictive stability.
* **Redundant/Unique Identifiers:** Features like `id` and `VIN` were unique identifiers carrying no statistical predictive weight.
* **Severe Outliers:** General distribution modeling highlighted severe noise in the target variable, including cars listed at `$0` or over `$3.7 billion`.

### 3. Data Preparation
To prepare the dataset for scikit-learn statistical modeling, the following pipeline operations were executed:
* **Feature Dropping:** Erased high-null and identifier columns (`VIN`, `size`, `id`).
* **Noise and Outlier Filtering:** Restriced rows to realistic market boundaries:
  * **Price:** Between $2,000 and $60,000.
  * **Odometer:** Between 100 and 250,000 miles.
  * **Year:** Vehicles manufactured between the years 2000 and 2022.
* **Algorithmic Pipeline Preprocessing:**
  * **Numeric Pathways (`year`, `odometer`):** Imputed missing entries using the `median` strategy and applied `StandardScaler` to align scales.
  * **Categorical Pathways (7 features):** Filled missing entries with a constant flag (`unknown`) and transformed text via `OneHotEncoder` into numerical columns of `1`s and `0`s.
 
## Model Evaluation Metrics & Interpretation

### Primary Metric Selection
Our primary evaluation metric for this model benchmark is **Mean Absolute Error (MAE)**. We also track **Root Mean Squared Error (RMSE)** and $R^2$ as secondary metrics to monitor variance and penalize larger prediction outliers.

### Rationale (Why MAE is the Best Choice Here)
We chose MAE as our main score because it makes the most sense in a real-world business context:
* **No Confusing Units:** Other popular math metrics, like Mean Squared Error (MSE), square the errors. This leaves you with units that make no practical sense, like "dollars squared."
* **Real-World Meaning:** MAE keeps things simple by measuring mistakes in normal, everyday dollars. 

> **What our MAE means:** 
> With our models achieving an MAE of **$4,962**, it simply means our price predictions are off by an average of **$4,962** compared to the actual sticker price of the car. This makes our model's performance incredibly easy to explain to dealership managers, sales teams, or everyday car buyers.

### Interpretation of the Results
Our final $R^2$ score sits at approximately **0.72** across all three models. This means our clean features (such as year, mileage, and condition) explain **72% of the variance** in used car prices. The remaining 28% of the price variation is likely dictated by unmeasured factors that were not in our dataset—such as a vehicle's accident history, its color, or individual wear-and-tear.

### Model Evaluation Findings & Selection
* **Minimal Performance Discrepancies:** During evaluation, we observed all 3 models (standard Linear Regression, Ridge, and Lasso) performed almost identically. This indicates that our feature engineering and preprocessing pipeline created highly stable, predictive features with no significant overfitting or redundancy issues. 
* **Preprocessing Success:** Ridge and Lasso shine when there are thousands of overlapping, messy features that confuse standard models. Because our features are already clean, standard Linear Regression is doing a great job on its own.
* **Model Recommendation:** Thus, in this scenario any of the 3 models can be chosen but since we used ridge to calculate the best and worst coefficients for car pricing we will recommend **Ridge Regression** (Tuned via `GridSearchCV` with an optimal alpha of `10.0`).

## Strategic Insights & Recommendations

By evaluating our trained Ridge model, we isolated the top weights influencing valuation.

### Top 5 Value Boosters (Inventory Sourcing Priorities)
These are the golden features that increase a car's price. When sourcing inventory, buy as many of these as possible:
* **I. Newer Model Year (+$5,749 impact):** Unsurprisingly, a vehicle’s age is the single biggest factor. For every standard unit jump toward a newer year, the value surges by roughly $5,750. Newer cars sell for a massive premium.
* **II. Diesel Engines (+$2,442 impact):** Diesel vehicles carry a heavy price premium over gas equivalents—boosting value by about $2,442.
* **III. 8-Cylinder Engines (+$1,518 impact):** Heavy-duty power sells. Cars or trucks boasting an 8-cylinder engine command $1,518 more on average.
* **IV. Pickup Trucks (+$1,295 impact):** Heavy utility vehicles are highly sought after. Adding a pickup to the inventory automatically commands a $1,295 premium.
* **V. Standard Trucks (+$1,280 impact):** Just like pickups, other truck varieties are a major value driver, bringing in an extra $1,281 in pricing power.

### Top 5 Value Killers (Inventory Purchasing Red Flags)
Avoid these features when buying inventory, or price them lower to move them off the lot quickly:
* **I. High Mileage (-$3,799 impact):** High odometer readings are a massive warning sign for buyers. Every standard unit increase in mileage drops the vehicle's value by nearly $3,800.
* **II. 4-Cylinder Engines (-$1,362 impact):** While fuel-efficient, smaller 4-cylinder engines drag down pricing power by $1,362 compared to larger engines.
* **III. Sedans (-$1,311 impact):** Traditional sedans are in low demand, pulling the vehicle's expected value down by $1,311.
* **IV. Standard Gas Engines (-$1,075 impact):** Standard gasoline engines face a price penalty of $1,076 compared to high-demand diesel alternatives.
* **V. Hatchbacks (-$945 impact):** Much like sedans, smaller hatchback models are less popular in this market segment, dragging prices down by $945.

---

##  Actionable Dealership Strategy

1. **Pivot Inventory Toward Utility:** Actively transition our dealership inventory away from slow-moving sedans and hatchbacks, and focus buying power on pickup trucks, standard trucks, and diesel engines.
2. **Prioritize Low Mileage Over All Else:** When evaluating two similar trade-ins, prioritize the vehicle with lower mileage. A high odometer reading hurts the value (-$3,800) far more than a slightly older model year.
3. **Market Large Engines and Diesels as Premium:** Create marketing campaigns highlighting the towing capability and durability of our 8-cylinder and diesel inventory to justify their higher retail prices.

---

## Next Steps

1. **Integrate an Automatic Appraisal Tool:** Deploy our Ridge Regression model as a lightweight appraisal calculator on our dealership's buying desk. Appraisers can input a trade-in's year, mileage, and type to instantly get a fair, data-backed purchase offer.
2. **Incorporate Vehicle Condition Metrics:** In our next data collection cycle, we should gather deeper vehicle health history (like accident records or previous owners) to see if we can explain the remaining 28% of price variance.
