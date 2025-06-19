# 🌳 Decision Trees: Basics & Math

## What is a Decision Tree?

A **Decision Tree** is a supervised learning algorithm used for classification and regression. It works by splitting data based on features to create a tree of decisions that leads to an outcome.

---

## 🧠 How Does It Work?

Imagine predicting if a Walmart store should restock a product:

```text
               [Units Sold > 1000?]
                   /         \
                Yes           No
            [Stock < 300?]    Restock = No
              /      \
          Yes        No
   Restock = Yes   Restock = No
```

Each decision node splits data based on a condition.

---

## ✂️ Splitting Criteria (Mathematics)

### 1. Gini Impurity (used in classification)

Measures how "mixed" the classes are in a node:

$$
Gini = 1 - \sum_{i=1}^{C} p_i^2
$$

Where:

- $C$ = number of classes  
- $p_i$ = proportion of samples of class $i$

**Example:** Suppose a node has 80% "Restock" and 20% "Don't Restock":

$$
Gini = 1 - (0.8^2 + 0.2^2) = 1 - (0.64 + 0.04) = 0.32
$$

Lower Gini → purer node → better split.

---

### 2. Information Gain (based on entropy)

$$
IG = Entropy(parent) - \sum_j \frac{N_j}{N} \cdot Entropy(child_j)
$$

Entropy for a binary class:

$$
Entropy = -p \log_2 p - (1-p) \log_2 (1-p)
$$

---

## ✂️ Pruning

Pruning is used to prevent overfitting by trimming nodes that add little predictive power.

- **Pre-pruning:** Stop tree early based on depth or minimum samples.
- **Post-pruning:** Build full tree, then remove weak branches.

---

# 🌲 Random Forest: Ensemble of Trees

A **Random Forest** is a collection (ensemble) of Decision Trees.

### ✅ Why Use It?

- Reduces overfitting.
- Improves accuracy and stability.
- Handles missing values and noisy data well.

---

## 🧪 How It Works (with Math)

- **Bagging:** Randomly sample the dataset with replacement to create multiple training sets.
- Train separate Decision Trees on each sample.

For predictions:
- **Classification:** majority voting
- **Regression:** average of outputs

**Walmart Example:**  
Let’s say you're predicting daily store traffic:

- **Feature set:** weather, day_of_week, promo, stock_level, etc.
- You build 100 trees using different bootstrap samples and random subsets of features.
- Each tree gives a prediction → final prediction is average (for regression) or vote majority (for classification).

---

# 🧠 Ensemble Learning: Bagging vs Boosting

## 1. Bagging (Bootstrap Aggregating)

- Build many models independently in parallel.
- Average results to reduce variance.
- Random Forest is a classic example.

> Think: “Let’s average many weak models to make a strong one.”

## 2. Boosting

- Build models sequentially, each one correcting the errors of the previous.
- Focus on hard-to-predict points.
- Final model is a weighted combination.

**Popular Algorithms:**
- AdaBoost
- Gradient Boosting Machines (GBM)
- XGBoost, LightGBM

> Think: “Let’s focus on mistakes and fix them step-by-step.”

---

## 📊 Comparison Table

| Aspect           | Bagging (e.g. Random Forest) | Boosting (e.g. XGBoost)      |
|------------------|------------------------------|------------------------------|
| Model Training   | Parallel                     | Sequential                   |
| Goal             | Reduce variance              | Reduce bias and variance     |
| Handles noise    | Better                       | May overfit noisy data       |
| Speed            | Faster (parallelizable)      | Slower (depends on sequence) |
| Example          | Random Forest                | XGBoost, LightGBM, AdaBoost  |

---

## 🔚 Summary

- **Decision Trees:** Easy to understand, but prone to overfitting.
- **Random Forests:** Combine many trees to improve generalization.
- **Bagging:** Focus on averaging out variance (Random Forest).
- **Boosting:** Focus on learning from errors (XGBoost, GBM).