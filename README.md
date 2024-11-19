# 🌟 Armut Service Recommendation System

This project builds a recommendation system for **Armut**, Turkey’s largest online service platform, using **Association Rule Learning (ARL)**. The goal is to recommend services to users based on their previous service history and patterns of service usage.

---

## 🚀 Project Overview

### 📝 Problem Statement
Armut connects service providers with users seeking services like cleaning, renovation, and moving. By analyzing historical service usage, this project aims to develop a recommendation system using ARL, enabling personalized service suggestions for users.

### 📊 Dataset
The dataset includes:
- **UserId**: Unique customer identifier  
- **ServiceId**: Anonymous services (e.g., sofa cleaning, furniture assembly)  
- **CategoryId**: Anonymous categories (e.g., cleaning, transportation)  
- **CreateDate**: Date and time of service purchase  

---

## 📂 Dataset Features

| Feature        | Description                                                       |
|----------------|-------------------------------------------------------------------|
| `UserId`       | Unique customer identifier                                        |
| `ServiceId`    | Anonymized service identifier under a specific category           |
| `CategoryId`   | Anonymized category identifier                                    |
| `CreateDate`   | Date and time the service was purchased                           |

---

## 🔧 Key Features

### 🛠 Tasks

1. **Data Preparation**:
   - Combine `ServiceId` and `CategoryId` to create a unique service identifier.
   - Define a **basket** as services purchased by a user in a given month.
   - Generate a unique `BasketID` for each user and month combination.
2. **Association Rule Learning**:
   - Use the Apriori algorithm to identify frequent itemsets.
   - Derive association rules from frequent itemsets.
3. **Service Recommendation**:
   - Implement a recommendation function to suggest services based on the last service purchased.

---

## 📈 Project Workflow

### 1️⃣ Data Preparation
- Combine `ServiceId` and `CategoryId` to create a new `Service` column (e.g., `2_4` for a unique service).
- Define baskets as monthly service groupings for each user:
  - Extract year and month from `CreateDate`.
  - Combine `UserId` and the extracted date to create a unique `BasketID`.

### 2️⃣ Generate Association Rules
- Create a pivot table with `BasketID` as rows and unique services as columns.
- Apply the **Apriori algorithm** to calculate frequent itemsets.
- Derive association rules from frequent itemsets, focusing on metrics like `support`, `confidence`, and `lift`.

### 3️⃣ Build Recommendation System
- Implement a function (`arl_recommender`) to:
  - Take a service ID as input.
  - Suggest related services based on high-lift association rules.

---

## 📊 Results

### 🎯 Example Recommendation
For a user who purchased service `2_0`, the following recommendations are generated:
```python
arl_recommender(rules, "2_0", 4)
```
**Output**:
- Recommended services: `['5_0', '7_2', '11_3']`

---

## 🛠 Tools and Libraries

- **Python**  
- **Pandas**  
- **Mlxtend** (for Apriori and Association Rules)  

---

## 🌟 Contribution

Contributions are welcome!  
Feel free to fork this repository, create issues, or submit pull requests for improvements.

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).
