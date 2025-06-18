# 🎯 What is K-Means Clustering?

**K-Means** is an unsupervised learning algorithm that:

- Groups similar data points into **K** clusters
- Assigns each point to the nearest cluster center (**centroid**)

It's like:

> "You give the algorithm a number K, and it tries to split the data into K groups, based on similarity."

---

## 🧠 Real-World Analogy 

Imagine a Walmart warehouse where all types of items are mixed up: electronics, clothes, food. You ask someone to group similar items into 3 sections — without knowing categories in advance.

They'll likely:

1. Pick 3 random spots (temporary group centers)
2. Group items by closeness to those spots
3. Move each group’s center to the middle
4. Repeat until the grouping makes sense

That’s what K-Means does!

---

## ⚙️ K-Means: Step-by-Step Algorithm

Given: dataset $X = \{x_1, x_2, ..., x_n\}$ and desired number of clusters $K$.

**Step 1: Initialization**  
Randomly select $K$ data points as initial centroids.

**Step 2: Assignment**  
For each point $x_i$, assign it to the nearest centroid:

$$
\text{Assign } x_i \text{ to cluster } j \text{ where: } j = \arg\min_{j} \|x_i - \mu_j\|^2 \quad \text{for all } j = 1 \text{ to } K
$$

This uses **Euclidean distance** to determine closeness.

**Step 3: Update Centroids**  
Recalculate the centroid (mean) of each cluster:

$$
\mu_j = \frac{1}{N_j} \sum x_i \quad \text{where } x_i \text{ belongs to cluster } j
$$

**Step 4: Repeat**  
Repeat Steps 2 and 3 until:

- Assignments no longer change, **or**
- Max iterations reached

---

## 📉 Objective of K-Means (the math part)

K-Means tries to minimize the total distance between points and their cluster centers, called **inertia** or **within-cluster sum of squares**:

$$
J = \sum_{j=1}^{K} \sum_{x_i \in C_j} \|x_i - \mu_j\|^2
$$

Where:

- $x_i$ is a data point
- $\mu_j$ is the centroid of its assigned cluster

**The goal:** Keep each cluster compact and separate.

---

## 🔍 Example (Simple 2D Data)

Let’s say we have customer data with:

- $x_1$: Monthly income
- $x_2$: Shopping frequency

K-Means will:

1. Choose 3 initial centers (if $K=3$)
2. Group similar customers (e.g., high-income frequent, low-income rare)
3. Update centers until stable

**Output:** 3 customer segments with centroids

---

## 📌 Things to Know

| Topic           | Explanation                                      |
|-----------------|--------------------------------------------------|
| Distance Metric | Usually Euclidean                                |
| K Selection     | Use Elbow Method or Silhouette Score             |
| Scaling         | Important to normalize data before K-Means       |
| Drawback        | Can struggle with non-spherical or overlapping clusters |
