# Mapping Digital Game Ecosystems: Steam & Backloggd Networks

This repository contains the processed datasets and graph files for a comparative study of game co-occurrence and co-citation networks

Originally focused on exploring the Steam ecosystem across four major regions (**Brazil, China, USA and Germany**), the project has since expanded to include data from **Backloggd**. By utilizing both platforms, this research aims to cross-validate findings, test topological invariance across different logging platforms, and provide a broader look at digital gaming cultures.

---

## Repository Structure

To accommodate the differente datasets, the graphs are divided into distinct directories:

* `/steam_network/`: Contains the regional network graphs based on Steam user data.
* `/backloggd_network/`: Contains the network graphs generated from Backloggd user data.

---

## How to Explore the Data (Gephi)

If you wish to analyze the specific clusters (tribes) within the provided `.gexf` files, please follow these steps using [Gephi](https://gephi.org/desktop/):

1. **Load Data**: Open the desired `.gexf` file from either the Steam or Backloggd folder.
2. **Colorization**: 
    * Navigate to the **Appearance** tab -> **Nodes** -> **Partition**.
    * Select the `community` attribute (calculated via Python Louvain) and click **Apply**.
3. **Filtering**:
    * Go to **Filters** -> **Attributes** -> **Partition** -> **community**.
    * Drag the filter to the **Queries** window.
    * Toggle the IDs (0, 1, 2, 3) to isolate specific tribes.
4. **Labels**: Use the **"T"** icon at the bottom of the window to toggle titles, or the click the Circle with an 'a' on top of it to show node labels. Scale labels by `weighted_degree` for better hierarchy.

> [!IMPORTANT]
> **Technical Note:** Gephi’s internal modularity tool may yield slightly different class results than the `community` attribute included in these files (especially in the Steam ones), which was pre-calculated using the Louvain method in Python.

---

## ⚠️ Research Status: Alpha Stage

This project is an ongoing exploration into the topological invariance of digital gaming cultures. Please be aware of the following limitations:

* **Data Imbalance**: There is a discrepancy in scale between regions. The USA graph contains ~50k more nodes than the Brazil/Germany sets due to higher network density in that sample, while the China Network contains ~100k more. With that said, those graphs may not be the best possible representation of the regional clusters using this method. Currently trying to improve on that.
* **Normalization**: I am currently refining a normalization pipeline to ensure cross-regional comparisons are performed on balanced node counts.
* **Edge Weighting**: The current weighting formula is being fine-tuned to mitigate "Super-node" outliers.

Changes 2 and 3 have already been applied in the Backloggd network, which is why it is the most recommended one to look at and represents the current status of the research the best.

---

## Meta-data Analysis

Beyond the visual representation, all calculated metrics and metadata from the Python pipeline are stored within the nodes' attributes. To view the raw data:

### Accessing the Data
Click on the **"Data Laboratory"** tab at the very top of the Gephi window. Here you can see the table with all game statistics.

### Key Attributes
* **Centrality Measures**: 
    * `weighted_degree`: The primary influence metric.
    * `degree`, `indegree_centrality` & `betweeness_centrality`.
* **Categorization**: 
    * `community` or `modularity class`: The tribe ID assigned by the algorithm.
    * `tag1`, `tag2`, `tag3`: Top Steam store and IGDB Backloggd tags. (warning, some of these might not have tags or just 1-2 tags)
* **Popularity Stats**: 
    * `num_players`: Count within the crawled sample.
    * `is_free`: Boolean status.
 
  As well as many, many other different metrics (especially on the Backloggd Network).

### Sorting & Filtering
* **Sort**: Click on any column header (e.g., `num_players`) to rank games.
* **Filter**: Use the **"Search"** box in the top right of the table to find specific titles or tags.

---
*This work is entirely amateurish in nature. Feedback on the methodology is welcome.*
