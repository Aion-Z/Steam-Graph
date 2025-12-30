# Mapping the Steam Ecosystem by use of Co-Citation

This repository contains the processed datasets and graph files for a comparative study of game co-occurrence networks across four major regions: **Brazil, China, USA, and Germany**.

---

## How to Explore the Data (Gephi)

If you wish to analyze the specific clusters (tribes) within the provided `.gexf` files, please follow these steps:

1. **Load Data**: Open the desired `.gexf` file from the repository.
2. **Colorization**: 
    * Navigate to the **Appearance** tab -> **Nodes** -> **Partition**.
    * Select the `community` attribute (calculated via Python Louvain) and click **Apply**.
3. **Filtering**:
    * Go to **Filters** -> **Attributes** -> **Partition** -> **community**.
    * Drag the filter to the **Queries** window.
    * Toggle the IDs (0, 1, 2, 3) to isolate specific tribes.
4. **Labels**: Use the **"T"** icon at the bottom of the window to toggle titles. Scale labels by `weighted_degree` for better hierarchy.

> [!IMPORTANT]
> **Technical Note:** Gephi’s internal modularity tool may yield slightly different class results than the `community` attribute included in these files, which was pre-calculated using the Louvain method in Python.

---

## ⚠️ Research Status: Alpha Stage

This project is an ongoing exploration into the topological invariance of digital gaming cultures. Please be aware of the following limitations:

* **Data Imbalance**: There is a discrepancy in scale between regions. The USA graph contains ~50k more nodes than the Brazil/Germany sets due to higher network density in that sample, while the China Network contains ~100k more. With that said, those graphs may not be the best possible representation of the regional clusters using this method. Currently trying to improve on that.
* **Normalization**: I am currently refining a normalization pipeline to ensure cross-regional comparisons are performed on balanced node counts.
* **Edge Weighting**: The current weighting formula is being fine-tuned to mitigate "Super-node" outliers.

I'm also currently working on expanding the project to other game ecosystems to prove/disprove findings and structure. 

---

## Meta-data Analysis

Beyond the visual representation, all calculated metrics and metadata from the Python pipeline are stored within the nodes' attributes. To view the raw data:

### Accessing the Data
Click on the **"Data Laboratory"** tab at the very top of the Gephi window. Here you can see the table with all game statistics.

### Key Attributes
* **Centrality Measures**: 
    * `weighted_degree`: The primary influence metric.
    * `degree` & `indegree_centrality`.
* **Categorization**: 
    * `community`: The tribe ID assigned by the algorithm.
    * `tag1`, `tag2`, `tag3`: Top Steam store tags. (warning, some of these might not have tags or just 1-2 tags)
* **Popularity Stats**: 
    * `num_players`: Count within the crawled sample.
    * `is_free`: Boolean status.

### Sorting & Filtering
* **Sort**: Click on any column header (e.g., `num_players`) to rank games.
* **Filter**: Use the **"Search"** box in the top right of the table to find specific titles or tags.

---
*This work is entirely amateurish in nature. Feedback on the methodology is welcome.*
