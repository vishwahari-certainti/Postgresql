# ShopEase Database Management Script

## Description

This Python script (db.py) provides a comprehensive solution for managing a retail shop database using PostgreSQL. It covers various database operations, from setting up the database schema and optimizing performance to data manipulation, advanced querying, and data export. The script is menu-driven, allowing users to interactively perform different tasks.

## Features

This script implements the following functionalities:

*   **Database Setup:**
    *   Creates tables for stores, employees, customers, suppliers, products, orders, order items, and payments.
    *   Creates indexes to optimize query performance.
    *   Creates views for top-selling products and store revenue.
    *   Creates triggers to enforce data integrity (e.g., prevent out-of-stock orders, audit employee deletions).

*   **Data Management:**
    *   Inserts sample data into all tables for testing and demonstration.
    *   Loads data from XLSX files into database tables.
    *   Performs CRUD (Create, Read, Update, Delete) operations using stored procedures.

*   **Advanced Querying:**
    *   Demonstrates Common Table Expressions (CTE) for recursive queries, like displaying employee hierarchies.
    *   Illustrates various JOIN operations (INNER, LEFT, RIGHT, FULL, SELF JOIN) for data retrieval across tables.
    *   Utilizes UNION and UNION ALL for combining result sets.
    *   Performs data pivoting (transposing data) to display monthly sales using crosstab.

*   **Data Modification and Deletion:**
    *   Updates data, such as increasing product prices, updating employee salaries, and adjusting product stock based on shipments.
    *   Deletes data, including inactive customers, orders (with cascading deletion of order items), and truncates audit tables.

*   **Data Export:**
    *   Exports monthly revenue per store to CSV or XLSX files.
    *   Exports a list of customers and their total spending to CSV or XLSX files.

## Prerequisites

Before running the script, ensure you have the following installed:

*   **Python 3.x**
*   **psycopg2:** PostgreSQL adapter for Python. Install using pip:
    ```bash
    pip install psycopg2-binary
    ```
*   **pandas:** Data analysis library for Python, used for XLSX and CSV export and XLSX import. Install using pip:
    ```bash
    pip install pandas openpyxl
    ```
*   **PostgreSQL:** Database server.
    *   Ensure PostgreSQL is installed and running.
    *   Create a database named ShopDetails (or modify DB_NAME in the script).
    *   Create a PostgreSQL user named postgres with a secure password (modify DB_USER and DB_PASSWORD in the script).

## Setup

1.  **Download the script:** Save the db.py Python script to your local machine.
2.  **Database Configuration:**
    *   Open the db.py file in a text editor.
    *   Modify the database connection details in the script if necessary to match your PostgreSQL setup:
    ```python
    DB_NAME = "ShopDetails"
    DB_USER = "postgres"
    DB_PASSWORD = "your_password"
    DB_HOST = "localhost"
    DB_PORT = "5432"
    ```
3.  **Install Extensions (tablefunc):** The pivot table functionality uses the tablefunc extension in PostgreSQL. The script attempts to create it if it doesn't exist. Superuser privileges might be required.

## How to Use

1.  **Run the script:** Open a terminal or command prompt, navigate to the directory where you saved db.py, and run:
    ```bash
    python db.py
    ```

2.  **Menu Options:** The script will display a numbered menu:
    
    1. Create tables
    2. Create indexes
    3. Create Views
    4. Create Triggers
    5. Insert Values into Table
    6. Load Xlsx to DB
    7. Common Table Expressions - (CTE)- Employee hierarchy
    8. Query Data using Joins (INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL JOIN, SELF JOIN)
    9. UNION and UNION ALL
    10. Update Data
    11. Pivot (Transpose Data)
    12. Delete Data
    13. CRUD Operations
    14. Data Export

3.  **Select a Task:** Enter the number corresponding to the task you want to perform and press *Enter*.

    *   Example: To create tables, enter 1 and press *Enter*.
    *   For data export, enter 14 and then choose export type (1 or 2) and file format (CSV or XLSX) when prompted.
    *   For loading data from XLSX (option 6), you will be prompted to enter the XLSX file path and the table name.

4.  **Follow Prompts:** The script will guide you through each selected task with further prompts if necessary.

## Tasks Covered and Menu Options Mapping

| Part | Task Description                                       | Menu Option |
|------|-------------------------------------------------|-------------|
| Part 1 | Create Database Tables                            | 1           |
| Part 2 | Create Indexes                                   | 2           |
| Part 3 | Create Views                                    | 3           |
| Part 3 | Create Triggers                                 | 4           |
| Part 4 | Insert Values into Tables                      | 5           |
| Part 4 | Import Data from CSV/XLSX                      | 6           |
| Part 5 | Common Table Expressions (CTE) - Employee hierarchy | 7           |
| Part 5 | Query Data using Joins                         | 8           |
| Part 5 | UNION and UNION ALL                            | 9           |
| Part 6 | Update Data                                    | 10          |
| Part 6 | Pivot (Transpose Data)                         | 11          |
| Part 6 | Delete Data                                    | 12          |
| Part 7 | CRUD Operations (Stored Procedures)            | 13          |
| Part 8 | Extract Results to CSV/XLSX (Data Export)      | 14          |

## File Exports

When using option 14 (Data Export), the script will generate the following files in the same directory as db.py:

*   **Monthly Revenue per Store:**
    *   monthly_store_revenue.csv (if CSV format is chosen)
    *   monthly_store_revenue.xlsx (if XLSX format is chosen)
    *   Contains monthly revenue data for each store, including 'Store Name', 'Month', 'Year', and 'Monthly Revenue'.

*   **Customer Total Spending:**
    *   customer_total_spending.csv (if CSV format is chosen)
    *   customer_total_spending.xlsx (if XLSX format is chosen)
    *   Contains a list of customers and their total spending, including 'Customer Name' and 'Total Spending'.

## Notes

*   **Error Handling:** The script includes basic error handling for database connections and operations. Check the console output for error messages if something goes wrong.
*   **Sample Data:** Option 5 inserts a significant amount of sample data. You can modify or extend the insert_sample_data function in the script to adjust the data being inserted.
*   **Security:** The provided database credentials in the script are for local development and testing purposes. *Do not use these credentials in production environments.* Implement proper security measures and credential management for production deployments.
*   **Dependencies:** Ensure all required Python libraries (psycopg2, pandas, openpyxl) are installed before running the script.
*   **PostgreSQL Setup:** Make sure your PostgreSQL server is running and configured correctly before running the script.


