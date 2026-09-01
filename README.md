# Python Finance Manager

A simple command-line personal finance management application built with Python. The application allows users to record income and expenses, view transactions within a selected date range, calculate financial summaries, and visualize financial activity using graphs.

The project uses CSV files for data storage, Pandas for data processing, and Matplotlib for visualization.

## Features

* Add new financial transactions
* Record both income and expenses
* Enter a custom transaction date
* Automatically use today's date when no date is provided
* Add transaction amounts
* Categorize transactions as Income or Expense
* Add descriptions to transactions
* View transactions within a specific date range
* Calculate total income
* Calculate total expenses
* Calculate net savings
* Display transactions in a formatted table
* Visualize income and expenses over time
* Automatically create the CSV database if it does not exist
* Store financial data locally

## Technologies Used

* Python
* Pandas
* Matplotlib
* CSV
* datetime

## Project Structure

```text
PYTHON-FINANCE-MANAGER/
│
├── main.py
├── data_entry.py
├── finance_data.csv
├── requirements.txt
└── README.md
```

## File Description

### `main.py`

The main application file.

It contains:

* The `CSV` class
* Transaction management
* CSV initialization
* Transaction filtering
* Financial calculations
* Data visualization
* Main application menu

### `data_entry.py`

Contains functions used to collect and validate user input.

The functions include:

```python
get_category()
get_date()
get_amount()
get_description()
```

These functions keep the input logic separate from the main application logic.

### `finance_data.csv`

This file is used to store all transactions.

The CSV structure is:

```text
date,amount,category,description
```

Example:

```csv
date,amount,category,description
01-09-2026,5000,Income,Freelance payment
02-09-2026,1200,Expense,Groceries
05-09-2026,500,Expense,Transport
```

### `requirements.txt`

Contains the external Python packages required to run the project.

```text
pandas
matplotlib
```

## Installation

### Prerequisites

Make sure you have Python installed on your computer.

You can check your Python version using:

```bash
python --version
```

or:

```bash
py --version
```

## Clone the Repository

Using GitHub CLI:

```bash
gh repo clone theycreate88/PYTHON-FINANCE-MANAGER
```

Or using Git:

```bash
git clone https://github.com/theycreate88/PYTHON-FINANCE-MANAGER.git
```

Navigate into the project:

```bash
cd PYTHON-FINANCE-MANAGER
```

## Install Dependencies

Install the required packages using:

```bash
pip install -r requirements.txt
```

Alternatively:

```bash
pip install pandas matplotlib
```

## Run the Application

Start the application using:

```bash
python main.py
```

On Windows, you can also use:

```bash
py main.py
```

## Application Menu

When the program starts, the following menu is displayed:

```text
1. Add a new Transaction

2. View Transaction and Summary within a date range
3. Exit

Enter Choice (1-3):
```

The user can choose one of three options.

## 1. Add a New Transaction

Select:

```text
1
```

The application asks for the following information:

```text
Enter Date (dd-mm-yy) or press Enter for today's Date:
Enter Amount:
Enter Category:
Enter Description:
```

Example:

```text
Enter Date (dd-mm-yy) or press Enter for today's Date: 01-09-2026
Enter Amount: 5000
Enter Category: Income
Enter Description: Freelance payment
```

The transaction is then added to `finance_data.csv`.

The application displays:

```text
Entry Added Successfully
```

## 2. View Transactions and Summary

Select:

```text
2
```

The application asks for:

```text
Enter Start Date:
Enter End Date:
```

For example:

```text
Enter Start Date: 01-09-2026
Enter End Date: 30-09-2026
```

The application filters the transactions and displays only transactions within the selected date range.

Example:

```text
Transactions from 01-09-2026 to 30-09-2026

      date  amount category       description
01-09-2026  5000.0   Income  Freelance payment
02-09-2026  1200.0  Expense             Groceries
05-09-2026   500.0  Expense             Transport
```

## Financial Summary

After displaying the transactions, the application calculates:

```text
Summary:

Total Income: $5000.00
Total Expense: $1700.00
Net Saving: $3300.00
```

The net savings calculation is:

```text
Net Saving = Total Income - Total Expense
```

For example:

```text
Total Income  = $5000
Total Expense = $1700

Net Saving = $5000 - $1700
           = $3300
```

## Data Visualization

After viewing transactions, the application asks:

```text
Do you want to see a plot (y/n)
```

Enter:

```text
y
```

to display a graph.

The graph is designed to show financial activity over time.

The graph contains:

* Date on the X-axis
* Amount on the Y-axis
* Income values
* Expense values
* A legend for the different transaction types

The application uses Matplotlib to generate the visualization.

## Data Processing

Pandas is used to process and analyze the transaction data.

When transactions are requested within a date range, the application:

1. Reads the CSV file.
2. Converts the date column into datetime objects.
3. Converts the entered start and end dates.
4. Filters transactions based on the selected date range.
5. Separates Income and Expense transactions.
6. Calculates the total income.
7. Calculates the total expenses.
8. Calculates the net savings.
9. Returns the filtered transaction data.

## CSV Management

The project uses a `CSV` class to handle financial data.

The class defines:

```python
CSV_FILE = "finance_data.csv"
COLUMNS = ["date", "amount", "category", "description"]
FORMAT = "%d-%m-%Y"
```

### CSV Initialization

The application checks whether the CSV file exists.

If it does not exist, a new CSV file is created with the required column names.

```python
CSV.intialize_csv()
```

### Adding Transactions

Transactions are added using:

```python
CSV.add_entry(date, amount, category, description)
```

The transaction is written to the CSV file using Python's `csv.DictWriter`.

### Retrieving Transactions

Transactions can be retrieved using:

```python
CSV.get_transactions(start_date, end_date)
```

This function filters transactions according to the selected date range and generates the financial summary.

## Application Workflow

```text
Start
  |
  v
Initialize CSV File
  |
  v
Display Main Menu
  |
  +------------------------+
  |                        |
  v                        v
Add Transaction       View Transactions
  |                        |
  v                        v
Get User Input        Enter Date Range
  |                        |
  v                        v
Save to CSV           Filter Transactions
                           |
                           v
                    Calculate Summary
                           |
                           v
                       Show Plot?
                       /       \
                     Yes        No
                      |          |
                      v          |
                 Display Graph   |
                      |          |
                      +----+-----+
                           |
                           v
                       Main Menu
                           |
                           v
                          Exit
```

## Example Usage

Suppose you add the following transactions:

```text
01-09-2026 | 50000 | Income  | Freelance Project
02-09-2026 | 5000  | Expense | Groceries
03-09-2026 | 2000  | Expense | Transport
05-09-2026 | 10000 | Expense | Shopping
```

The application calculates:

```text
Total Income: $50000.00
Total Expense: $17000.00
Net Saving: $33000.00
```

## Error Handling

The application handles the case where the CSV file does not exist by automatically creating it.

If no transactions are found within the selected date range, the application displays:

```text
No transactions found in given date range
```

Invalid menu selections result in:

```text
Invalid Choice!
```

## Learning Objectives

This project demonstrates several important Python programming concepts:

### Python Fundamentals

* Variables
* Functions
* Conditional statements
* Loops
* User input
* String formatting

### Object-Oriented Programming

* Classes
* Class attributes
* Class methods
* Encapsulation of CSV-related functionality

### File Handling

* Reading CSV files
* Writing CSV files
* Appending data
* Creating files

### Data Analysis

* Pandas DataFrames
* Filtering data
* Data aggregation
* Date-based filtering
* Calculating totals

### Data Visualization

* Matplotlib
* Line charts
* Plotting time-based data
* Chart labels and legends

## Current Limitations

The current version is intentionally simple and has some limitations:

* It is a command-line application.
* Data is stored in a local CSV file.
* There is no user authentication.
* Transactions cannot currently be edited.
* Transactions cannot currently be deleted.
* There is no monthly budget system.
* There is no cloud synchronization.
* There is no database such as SQLite or PostgreSQL.
* Financial data is not encrypted.

## Future Improvements

Possible improvements include:

* Add transaction editing
* Add transaction deletion
* Add transaction search
* Add monthly budgets
* Add spending limits
* Add budget alerts
* Add category-wise expense reports
* Add monthly financial reports
* Add pie charts
* Add bar charts
* Add income versus expense comparisons
* Export reports to PDF
* Replace CSV storage with SQLite
* Add a graphical user interface
* Build a web-based version
* Add user authentication
* Add cloud database support
* Add multiple user accounts
* Add recurring transactions
* Add financial dashboards

## Contributing

Contributions are welcome.

To contribute:

1. Fork the repository.
2. Create a new branch.

```bash
git checkout -b feature-name
```

3. Make your changes.
4. Commit your changes.

```bash
git add .
git commit -m "Add new feature"
```

5. Push the branch.

```bash
git push origin feature-name
```

6. Open a Pull Request.

## License

This project is open-source and available for educational purposes.

## Author

**Abdul Basit**

GitHub:

`https://github.com/theycreate88`

## Acknowledgements

This project was created as a Python practice project to understand file handling, data processing, object-oriented programming, and data visualization.

## Repository

**PYTHON-FINANCE-MANAGER**

```text
https://github.com/theycreate88/PYTHON-FINANCE-MANAGER
```
