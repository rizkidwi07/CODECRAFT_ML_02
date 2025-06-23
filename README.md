# Customers of a Retail Store based on Their Purchase History with K-Means Clustering

## Project Overview

This project performs customer segmentation on the "Mall Customers" dataset using the K-Means clustering algorithm. The goal is to group customers into distinct segments based on their annual income and spending habits. This type of analysis is valuable for businesses to better understand their customer base and tailor marketing strategies to different segments.

The accompanying Python script, `customer_segmentation.py`, automates the entire process, from data loading and preparation to model training and visualization of the final clusters.

## How to Run the Script

1.  **Prerequisites**:
    * Python 3.x
    * The following Python libraries installed:
        * `pandas`
        * `numpy`
        * `scikit-learn`
        * `matplotlib`
        * `seaborn`
    You can install these libraries using pip:
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn
    ```

2.  **Dataset**:
    * Ensure the `Mall_Customers.csv` file is in the same directory as the `customer_segmentation.py` script.

3.  **Execution**:
    * Open a terminal or command prompt, navigate to the project directory, and run the script using the following command:
    ```bash
    python customer_segmentation.py
    ```
    * The script will execute the analysis and display two plots: the Elbow Method graph and the final customer segments scatter plot.

---

## Process Breakdown

The script follows a standard machine learning workflow for clustering, which can be broken down into the following steps:

### 1. Importing Libraries

The script begins by importing the necessary libraries for data handling, clustering, and visualization:
- **pandas**: For loading and manipulating the dataset.
- **numpy**: For numerical operations, especially with the data array.
- **scikit-learn**: For implementing the K-Means clustering algorithm.
- **matplotlib & seaborn**: For creating the visualizations (plots).

### 2. Loading and Preparing the Data

The `Mall_Customers.csv` dataset is loaded into a pandas DataFrame. For this analysis, we are interested in segmenting customers based on two key features:
- **Annual Income (k$)**
- **Spending Score (1-100)**

These two columns are extracted from the DataFrame and stored in a NumPy array `X`, which will be used as the input for the K-Means algorithm.

### 3. The Elbow Method: Finding the Optimal K

To apply K-Means clustering, we first need to determine the optimal number of clusters (K). The script uses the **Elbow Method** for this purpose.

- **Process**: The algorithm is run for a range of K values (from 1 to 10). For each K, the **Within-Cluster Sum of Squares (WCSS)** is calculated. WCSS is the sum of the squared distances between each data point and its cluster's centroid.
- **Result**: A plot of WCSS against the number of clusters is generated. This plot typically shows a sharp "elbow" at the point where increasing the number of clusters no longer leads to a significant decrease in WCSS.

For this dataset, the elbow is clearly visible at **K=5**, indicating that five is the optimal number of clusters.

<div><img src="https://github.com/rizkidwi07/Source/raw/main/elbow%20method.png") width="1000"/></div><br/>

### 4. Training the K-Means Model

With the optimal K value identified, the K-Means model is trained using `n_clusters=5`. The `fit_predict` method is used to both train the model on the data `X` and assign each data point to one of the five clusters. The resulting cluster labels (from 0 to 4) are stored in the `y_kmeans` variable.

### 5. Visualizing the Segments

The final step is to visualize the customer segments. A scatter plot is created with:
- **X-axis**: Annual Income
- **Y-axis**: Spending Score

Each data point is colored according to its assigned cluster, making it easy to see the distinct groups. The centroids of each cluster are also plotted (in yellow) to show the center of each segment.

---

## Results and Interpretation

The K-Means algorithm successfully identifies five distinct customer segments:

<div><img src="https://github.com/rizkidwi07/Source/raw/main/cluster%20of%20customers.png") width="1000"/></div><br/>

The five clusters can be interpreted as follows:

-   **Cluster 1 (Standard)**: Customers with average annual income and average spending scores. They form a significant portion of the customer base.

-   **Cluster 2 (Careful)**: Customers with high annual income but low spending scores. These customers are cautious with their spending despite having the financial capacity.

-   **Cluster 3 (Target)**: Customers with high annual income and high spending scores. This is often the most desirable segment for marketing efforts, as they are both willing and able to spend.

-   **Cluster 4 (Careless)**: Customers with low annual income but high spending scores. This group may be less financially stable but are frequent spenders.

-   **Cluster 5 (Sensible)**: Customers with low annual income and low spending scores. They are budget-conscious and spend cautiously.

This segmentation provides valuable insights that can inform targeted marketing campaigns, product recommendations, and other business strategies.
