# -Week-3-Module-
Implementation of Merge Sort and Quick Sort algorithms for the Week 3 module.
# Merge Sort & Quick Sort - Technical Reference

This section contains the short logic, core approach, and step-by-step dry runs for the algorithmic problems covering **Merge Sort** and **Quick Sort**.

---

## ── TOPIC 1: MERGE SORT ──

### 1. Rank Student by Marks
* **Logic & Approach:** Uses a divide-and-conquer strategy. It recursively divides the array of marks into halves until single-element subarrays are reached, then merges them back in ascending order using a temporary buffer.
* **Dry Run:**  
  * **Input Array:** `[78, 45, 92, 34, 67, 81]` ($N = 6$)
  * **Splitting Phase:** Recursively breaks down into individual elements: `[78]`, `[45]`, `[92]`, `[34]`, `[67]`, `[81]`.
  * **Merge (Left Half):** 
    * `[78]` & `[45]` merge $\rightarrow$ `[45, 78]`
    * `[45, 78]` & `[92]` merge $\rightarrow$ `[45, 78, 92]`
  * **Merge (Right Half):** 
    * `[34]` & `[67]` merge $\rightarrow$ `[34, 67]`
    * `[34, 67]` & `[81]` merge $\rightarrow$ `[34, 67, 81]`
  * **Final Merge:** Combines `[45, 78, 92]` and `[34, 67, 81]` sequentially by comparing front elements.
  * **Result:** `[34, 45, 67, 78, 81, 92]`

### 2. Organizing Product Prices
* **Logic & Approach:** Implements standard Merge Sort on an array of product prices. The list splits into smaller parts, sorts each part recursively, and combines them back using a two-pointer approach to maintain an ascending price sequence.
* **Dry Run:**  
  * **Input Array:** `[2500, 1500, 4000, 3000, 1000]` ($N = 5$)
  * **Split Phase:** Separates into Left `[2500, 1500, 4000]` and Right `[3000, 1000]`.
  * **Left Sorting:** `[2500, 1500]` becomes `[1500, 2500]`, then merges with `[4000]` $\rightarrow$ `[1500, 2500, 4000]`.
  * **Right Sorting:** `[3000]` and `[1000]` merge directly $\rightarrow$ `[1000, 3000]`.
  * **Final Merge:** Sequentially compares elements from both sorted blocks.
  * **Result:** `[1000, 1500, 2500, 3000, 4000]`

### 3. Sort Employee Records by Salary
* **Logic & Approach:** Sorts employee salaries in ascending order using Merge Sort. Once sorted, statistical values are extracted instantly using array index lookup: Lowest salary is at index `0`, Highest salary is at index `N-1`, and the salary range is calculated as $\text{Highest} - \text{Lowest}$.
* **Dry Run:**  
  * **Input Array:** `[45000, 25000, 70000, 50000, 30000, 90000, 60000]` ($N = 7$)
  * **Sorting Step:** Merge Sort processes and transforms the array to: `[25000, 30000, 45000, 50000, 60000, 70000, 90000]`.
  * **Stats Extraction:**
    * **Lowest Salary:** `Salary[0]` = `25000`
    * **Highest Salary:** `Salary[6]` = `90000`
    * **Difference:** $90000 - 25000 = 65000$

---

## ── TOPIC 2: QUICK SORT ──

### 1. Race Timing Analysis
* **Logic & Approach:** In-place sorting using the Lomuto Partitioning strategy. It designates the last element as a pivot, rearranges smaller elements to its left, positions the pivot in its correct intermediate index, and recursively sorts both halves.
* **Dry Run:**  
  * **Input Array:** `[55, 49, 62, 58, 45, 51]` ($N = 6$)
  * **Partition 1:** `pivot = 51`. Elements smaller than 51 (`49`, `45`) swap to the front. Swap pivot into its absolute index position.
    * Array becomes: `[49, 45, 51, 58, 55, 62]`. Pivot sits at index `2`.
  * **Left Sub-Sort:** `[49, 45]` chooses `45` as pivot $\rightarrow$ sorts to `[45, 49]`.
  * **Right Sub-Sort:** `[58, 55, 62]` chooses `62` as pivot $\rightarrow$ smaller elements (`55, 58`) remain left $\rightarrow$ sorts to `[55, 58, 62]`.
  * **Result:** `[45, 49, 51, 55, 58, 62]`

### 2. Organizing Library Book IDs
* **Logic & Approach:** Performs ascending Quick Sort. It partitions unique library book IDs around a pivot element so that smaller numerical values shift left, followed by recursive sub-partition execution.
* **Dry Run:**  
  * **Input Array:** `[1025, 1001, 1050, 1010, 1005]` ($N = 5$)
  * **Partition 1:** `pivot = 1005`. The value `1001` is smaller and swaps with `1025`. Pivot swaps into position index `1`.
    * Array becomes: `[1001, 1005, 1050, 1010, 1025]`.
  * **Sub-sorting Phase:** 
    * Left side `[1001]` is a single element (base case).
    * Right side `[1050, 1010, 1025]` chooses `1025` as pivot $\rightarrow$ reorders to `[1010, 1025, 1050]`.
  * **Result:** `[1001, 1005, 1010, 1025, 1050]`

### 3. Online Store Sales Ranking
* **Logic & Approach:** Utilizes an ascending Quick Sort routine followed by a reverse-engineered print tracking system. To get descending outputs, the sorted array is traversed from the end (`N-1` down to `0`). The top 3 indexes are captured to display the best-performing values and calculate their average.
* **Dry Run:**  
  * **Input Array:** `[1200, 5000, 3000, 2500, 7000, 4500]` ($N = 6$)
  * **Sorting Step:** Quick Sort arranges the array ascendingly: `[1200, 2500, 3000, 4500, 5000, 7000]`.
  * **Reverse Output Loop:** Iterating from the end backward prints the descending ranking: `7000 5000 4500 3000 2500 1200`.
  * **Top 3 & Average:** 
    * Captures the last three values: `7000`, `5000`, and `4500`.
    * **Sum Calculation:** $7000 + 5000 + 4500 = 16500$
    * **Average Calculation:** $16500 / 3 = 5500$
