## 📊 Exploratory Data Analysis

### 1. Customer Demographics
First, I analyzed the basic demographic makeup of the customer base.
![Demographic Distribution](outputs/figures/No_Senior_Citizen_Distribution.png)

**Key Insights:**
* **Gender Balance:** The customer base is split almost equally between male and female.
* **Senior Citizens:** Seniors represent a small minority of the total customer base, indicating that the service is primarily used by younger or middle-aged demographics.

---

### 2. Household Composition & Segmentation
I investigated the relationship between having a partner and having dependents to better understand household "stickiness."
![Partner vs Dependents](outputs/figures/Partner_Distribution_by_Dependents.png)

**Key Insights:**
* **The "Independent" Segment:** The largest single group consists of customers with no partner and no dependents. Historically, these "single" households are often higher churn risks.
* **Childless Couples:** Among customers with a partner, nearly 50% do not have dependents.
* **Single Parents:** This is the smallest segment in the dataset, showing that customers without partners rarely have dependents in this particular telco base.

---

### 3. 🛠️ Service Impact on Retention

I analyzed 9 different services to identify which ones act as "Anchors" (keeping customers loyal) and which are "Churn Magnets."

![Service Churn Analysis](outputs/figures/Service_Distribution_by_Churn.png)

### 📊 Service Analysis Summary

| Service Category | Impact on Churn | Business Insight |
| :--- | :--- | :--- |
| **Fiber Optic Internet** | **High Risk** | Highest churn rate in the dataset; suggests pricing or stability issues. |
| **Online Security** | **High Retention** | Subscribed users are significantly less likely to leave (Peace of Mind). |
| **Tech Support** | **High Retention** | Acts as a strong "Anchor" service for long-term loyalty. |
| **Streaming Services** | **Moderate** | Associated with lower churn, likely due to the "Entertainment Bundle" effect. |
| **Phone/Multiple Lines** | **Neutral** | Shows no significant statistical difference in churn behavior. |


**Key Takeaway:** The data suggests that "Protection" and "Support" services are the strongest drivers of customer retention. Moving customers from "DSL" to "Fiber" without addressing the high churn rate could be a financial risk for the company.

---

During the Exploratory Data Analysis (EDA), it became clear that **Internet Service Type** is not just a standalone feature, but a "deciding factor" that influences the behavior of all other variables.

### 🔍 Why Internet Service is the Primary Segment:
* **Feature Interdependence:** The availability and utility of "Value-Added Services" (Online Security, Streaming, etc.) are entirely dependent on whether a customer has an internet connection.
* **The "Confounding" Effect:** Customers with **No Internet Service** show high loyalty despite having zero add-on services. Without segmenting by `InternetService`, this group would "mask" the high churn risk of internet-using customers with low service counts.
* **Fiber Optic vs. DSL:** Even when subscribed to the same number of total services, Fiber Optic customers exhibit significantly higher churn rates than DSL customers, suggesting that technology type is a stronger driver of dissatisfaction than "bundling" is of loyalty.

---

### 📉 The "Bundle Effect" Segmented by Service Type
I visualized the relationship between the number of services and churn probability, using **Internet Service** as the grouping variable (`hue`) to reveal these hidden trends.

![Bundle Effect Final](outputs/figures/Churn_Rate_by_Total_Services.png)

**Key Discovery:** For **Fiber Optic** users, the "Danger Zone" is having 0 or 1 service (Churn > 40%). For **No Internet** users, having 0 services is a "Safe Zone" (Churn < 10%). This confirms that internet type is the most critical segmenting factor for our predictive model.

---

