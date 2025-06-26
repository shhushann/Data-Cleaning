# CustomerDataExtractor

`CustomerDataExtractor` is a Python class designed to load, clean, and transform nested customer order data into a flat, analysis-ready Pandas DataFrame. It handles data inconsistencies, cleans fields like prices and quantities, resolves product categories, and marks VIP customers based on an external file.

---

## Features

- Loads pickled customer order data and VIP customer IDs from files.
- Cleans and normalizes prices, quantities, order IDs, and categories.
- Flattens nested customer and order information into a structured DataFrame.
- Flags VIP customers using a VIP list.
- Outputs a DataFrame with specified columns and strict data types ready for analysis.

---


## Installation

1. Clone this repository or copy the class code to your project.

2. Install required Python packages using the provided `requirements.txt`:

```bash
pip install -r requirements.txt
