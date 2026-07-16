# Practical_Application_11.1

Required Assignment 11.1: What Drives the Price of a Car?

Link to [https://github.com/Suraj-BH/Practical_Application_11.1/blob/main/prompt_II.ipynb]

## Findings

### 1. Business Understanding (The Problem)
Used car dealerships face a constant challenge: paying too much for trade-ins or pricing vehicles poorly on the lot. To maximize profit margins, we need a data-driven strategy to instantly know which vehicle features command a premium and which ones drastically hurt a vehicle's resale value.

### 2. What Actually Drives Prices Up? (Top 5 Value Boosters)
These are the golden features that increase a car's price. When sourcing inventory, buy as many of these as possible:

*   **I. Newer Model Year (+$5,750 impact):** Unsurprisingly, a vehicle’s age is the single biggest factor. For every standard unit jump toward a newer year, the value surges by roughly $5,750. Newer cars sell for a massive premium.
*   **II. Diesel Engines (+$2,443 impact):** Diesel vehicles carry a heavy price premium over gas equivalents—boosting value by about $2,443.
*   **III. 8-Cylinder Engines (+$1,518 impact):** Heavy-duty power sells. Cars or trucks boasting an 8-cylinder engine command $1,518 more on average.
*   **IV. Pickup Trucks (+$1,295 impact):** Heavy utility vehicles are highly sought after. Adding a pickup to the inventory automatically commands a $1,295 premium.
*   **V. Standard Trucks (+$1,281 impact):** Just like pickups, other truck varieties are a major value driver, bringing in an extra $1,281 in pricing power.

### 3. What Drags Prices Down? (Top 5 Value Killers)
Avoid these features when buying inventory, or price them lower to move them off the lot quickly:

*   **I. High Mileage (-$3,799 impact):** High odometer readings are a massive warning sign for buyers. Every standard unit increase in mileage drops the vehicle's value by nearly $3,800.
*   **II. 4-Cylinder Engines (-$1,362 impact):** While fuel-efficient, smaller 4-cylinder engines drag down pricing power by $1,362 compared to larger engines.
*   **III. Sedans (-$1,311 impact):** Traditional sedans are in low demand, pulling the vehicle's expected value down by $1,311.
*   **IV. Standard Gas Engines (-$1,076 impact):** Standard gasoline engines face a price penalty of $1,076 compared to high-demand diesel alternatives.
*   **V. Hatchbacks (-$945 impact):** Much like sedans, smaller hatchback models are less popular in this market segment, dragging prices down by $945.

---

### Actionable Recommendations
1. **Pivot Inventory Toward Utility:** Actively transition our dealership inventory away from slow-moving sedans and hatchbacks, and focus buying power on pickup trucks, standard trucks, and diesel engines.
2. **Prioritize Low Mileage Over All Else:** When evaluating two similar trade-ins, prioritize the vehicle with lower mileage. A high odometer reading hurts the value (-$3,800) far more than a slightly older model year.
3. **Market Large Engines and Diesels as Premium:** Create marketing campaigns highlighting the towing capability and durability of our 8-cylinder and diesel inventory to justify their higher retail prices.

---

### Next Steps
1. **Integrate an Automatic Appraisal Tool:** Deploy our Ridge Regression model as a lightweight appraisal calculator on our dealership's buying desk. Appraisers can input a trade-in's year, mileage, and type to instantly get a fair, data-backed purchase offer.
2. **Incorporate Vehicle Condition Metrics:** In our next data collection cycle, we should gather deeper vehicle health history (like accident records or previous owners) to see if we can explain the remaining 28% of price variance.
