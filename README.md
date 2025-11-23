# 📦 Minimising Costs by Improving Service Point Locations

**Logistics Optimization Study** | **Operations Research & Network Design**

***

## NOTE: The code file is 60MB, therefore you can dowload it from my google drive: https://drive.google.com/drive/folders/194BonnwPkfZw-T5tem7sKZtIZc1z5GQa?usp=sharing

## Executive Summary

This project presents a strategic optimization solution to address the challenge of managing a surge in package deliveries within a logistics network. The core objective was to **minimize annual operating costs** while maintaining efficient service by redesigning the existing service point network.

The solution proposes expanding the current 14 service points to a network of **27 optimized locations** with reduced individual capacities. This strategic shift encourages higher customer pick-up rates, significantly reducing the expensive and carbon-intensive home delivery volumes.

### Key Results
* 💰 **Cost Savings:** Estimated annual savings of approximately **€150,000** (a 12.3% reduction in operational costs).
* 🌐 **Network Redesign:** Expansion from 14 to **27** optimally placed service points.
* 🌱 **Sustainability:** Reduction in total travel distance, promoting a more sustainable logistics chain.

***

## The Problem

The existing network of 14 service points was no longer capable of handling the increasing volume of packages resulting from the growth of e-commerce. This strain led to high last-mile delivery costs, suboptimal service point placement relative to current demand, and increased carbon footprint from excessive home deliveries.

***

## Solution and Methodology in Code

The analysis in the `Team4, Final Code-1.ipynb` notebook follows a sophisticated, multi-stage approach combining network analysis, predictive demand modeling, and combinatorial optimization.

### 1. Network Analysis and Preprocessing
* **Dijkstra's Algorithm:** The project first constructs the underlying road network using the `Nodes data` and `Edges data`. **Dijkstra's Algorithm** is then employed to calculate the **shortest travel distance** between every demand node (customer location) and every potential service point location. This comprehensive distance matrix forms the foundation for all subsequent cost and behavioral modeling.

### 2. Customer Behavior and Predictive Modeling
* **Pick-up Probability Model:** A critical component of the model is predicting customer choice. A statistical model (likely derived from historical data) is used to estimate the **probability** that a customer will choose to **pick up** their parcel at the nearest service point. This probability is modeled as a function inversely related to the distance a customer must travel. This prediction determines the volume of expensive home deliveries versus cheaper service point pick-ups for any given network design.

### 3. Optimization using Simulated Annealing
* **Simulated Annealing:** Due to the massive number of potential service point combinations (a complex location-allocation problem), the **Simulated Annealing** heuristic is used to efficiently search for the globally optimal network design of **27 service points**. This method iteratively explores solutions, using a **temperature parameter** to guide the search by accepting non-improving solutions early on, ensuring a comprehensive search across the entire solution space.
* **Optimal Capacity:** The code includes logic to calculate the **optimal capacity** for each selected service point within the final network, ensuring efficient allocation of predicted pick-up volumes.

***

## Assumptions and Cost Model

The optimization process is driven entirely by a comprehensive **Cost Function** that the Simulated Annealing algorithm seeks to minimize. This function is built on the following key financial and operational assumptions:

### 1. The Total Cost Function
The objective function (`total_cost`) is defined as the sum of three primary annual cost components:

$$
\text{Total Cost} = \sum (\text{Variable Delivery Costs}) + \sum (\text{Fixed Location Costs}) + \sum (\text{Pick-up Handling Costs})
$$

* **Fixed Location Costs ($€10,000 \times \text{Number of Service Points}$):** The model assumes a fixed annual cost of **€10,000** for establishing and maintaining each service point in the network, regardless of its volume.
* **Pick-up Handling Costs ($\text{Total Annual Pick-up Volume} \times \mathbf{€0.10}$):** This cost is applied to every parcel that is successfully picked up by a customer. The cost factor used in the code is **€0.10 per parcel picked up**.
* **Variable Delivery Costs ($\sum \text{costs of locations}$):** This is the most complex component, representing the cost incurred for all parcels that are **home-delivered** (not picked up), which is highly dependent on the travel distance and volume for those deliveries.

### 2. Operational Assumptions
* **Fixed Cost Parameters:** The numerical values for fixed location costs (€10,000) and pick-up handling costs (€0.10) are assumed to be fixed for the duration of the analysis.
* **Accuracy of Predictive Model:** The cost minimization hinges on the assumption that the customer behavior model accurately predicts pick-up rates based on the proximity of new service points.

***

## Data Files Required 💾

To successfully run the analysis in the `Team4, Final Code-1.ipynb` notebook, the following data files must be placed in the same directory:

1.  **`data_Maastricht (2).xlsx`** (or a similar version of the primary dataset). This Excel file is expected to contain the following sheets:
    * `Nodes data`
    * `Edges data`
    * `Squares data`
    * `Service locations data`
    * `At-Home Deliveries`
    * `Service Point Parcels Picked Up`

2.  **`node_service_df.csv`**
3.  **`distances_nodes_service_points.csv`**

***

## How to Run the Project

1.  **Clone the Repository:**
    ```bash
    git clone [YOUR-REPOSITORY-URL]
    cd [your-repository-name]
    ```
2.  **Install Dependencies:** Ensure all required Python libraries (including `pandas`, `numpy`, `networkx`, `matplotlib`, etc.) are installed in your environment.
3.  **Place Data Files:** Add the three required data files (`.xlsx` and two `.csv` files) into the repository directory.
4.  **Execute the Notebook:** Open and run all cells in the `Team4, Final Code-1.ipynb` file using a Jupyter environment to replicate the network optimization and cost analysis.
