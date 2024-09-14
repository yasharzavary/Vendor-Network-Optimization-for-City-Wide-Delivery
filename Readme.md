# Vendor Network Optimization for City-Wide Delivery

This project focuses on optimizing the selection of vendors for city-wide delivery services, taking into account both user coverage and vendor performance scores. By selecting the most optimal vendors from a pool, the goal is to ensure maximum coverage of users while maintaining high vendor quality, as rated by users.

## Project Overview

In a city with multiple vendors and users, the aim is to optimize the selection of vendors such that:
1. **User coverage** is maximized, ensuring that most users are within the service range of selected vendors.
2. **Vendor scores** are maximized, ensuring that the selected vendors are the ones with the highest ratings from users.

This project utilizes **linear programming** to solve the optimization problem. We create a distance matrix between users and vendors and apply linear programming techniques to find the best combination of vendors that satisfy both criteria.

## Key Features

- **Linear Programming**: The main approach used for vendor optimization, balancing both user coverage and vendor scores.
- **Dynamic Vendor Selection**: The number of vendors to be selected can be customized, depending on business needs.
- **Blacklist and Preferred Vendors**: Certain vendors can be excluded from the results or pre-selected, based on external business rules.
- **Map Visualization**: Vendor locations are displayed on a map before and after the optimization, allowing for easy comparison of results.

## Datasets

This project makes use of two primary datasets in CSV format:
1. **`vendors.csv`**: Contains the following information for each vendor:
   - Vendor location (latitude and longitude).
   - Vendor performance score (based on user feedback).
   - Status bar indicating the vendor’s selection status:
     - `-1`: Vendor is blacklisted and will not be selected.
     - `1`: Vendor is pre-selected and will always be included.
     - `0`: Vendor is available for selection based on the optimization algorithm.
   
2. **`sessions.csv`**: Contains data on user sessions, including:
   - User location (latitude and longitude).
   - Number of users in each location, which helps determine the user coverage.

## Installation & Setup

To run this project, you will need **Python 3.11** or an older version and the required dependencies listed in the project.

### Steps:
1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/vendor-network-optimization.git
   ```
2. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the Jupyter notebook to execute the project.

## Usage

The main function in this project is `optimize_vendors`, where you can define the number of vendors you want to select.

### Example:

You have 5 vendors in the city, and over time, users have provided scores for these vendors. The task is to select 3 vendors that maximize user coverage and vendor scores. This project will handle the optimization and present the results on a map, showing both the pre- and post-optimization locations of the vendors.

### Customization:

- You can adjust the **number of vendors** to select by modifying the input to the `optimize_vendors` function.
- The **vendor status** can be customized in the `vendors.csv` file to blacklist or pre-select specific vendors.

## Alternative Approaches

In addition to the linear programming approach used in this project, there are other potential ways to solve the vendor optimization problem:

### Graph Modeling
One alternative method is to model the problem as a graph, where:
- **Vendors and users** are represented as nodes.
- **Edges** represent the connections between vendors and the users they can serve.

By applying graph algorithms like **Prim's algorithm**, it is possible to find a minimal spanning tree that maximizes user coverage while also considering vendor scores. Although this approach is effective, the linear programming model used here provides more flexibility for balancing multiple objectives such as coverage and vendor quality.

## Map Visualization

One of the key features of this project is the ability to visualize the vendors before and after the optimization on a map. This helps in understanding the geographic distribution of the vendors and how the optimization affects their locations.

---