# Expense Tracker (Python CLI)

A small command-line application to record, search, summarize and export daily expenses.
It uses only the Python standard library, so there is nothing to install.

Built as the project of my **Python Internship** at Slash Mark IT Solutions (OPC) Pvt. Ltd.
(10 June 2026 - 10 August 2026) - Duddugunta Sridhar, B.Tech CSE, Mohan Babu University.

## Features

- Add expenses with an amount, category, note and date
- List expenses, filtered by category and/or month
- Delete an expense by its id
- Summary of spending per category with a text bar chart
- Export expenses to a CSV file
- Data stored in a JSON file (written safely, so the file is never half-written)
- Input validation with clear error messages and exit codes
- 18 unit tests

## Concepts practised

| Python topic | Where it is used |
|---|---|
| Functions, modules and packages | `expense_tracker/` package |
| Data classes and validation | `models.py` |
| File handling (JSON, CSV) | `storage.py`, `tracker.py` |
| Exception handling | custom `StorageError` and `ExpenseNotFoundError` |
| Object-oriented programming | `Expense`, `JsonStorage`, `ExpenseTracker` classes |
| Command-line programs (`argparse`) | `cli.py` |
| Unit testing (`unittest`) | `tests/test_tracker.py` |

## Project structure

```
expense-tracker/
├── main.py                  # entry point
├── expense_tracker/
│   ├── __init__.py
│   ├── models.py            # Expense data class
│   ├── storage.py           # JSON storage
│   ├── tracker.py           # ExpenseTracker (business logic)
│   └── cli.py               # argparse command-line interface
├── tests/
│   └── test_tracker.py      # unit tests
├── requirements.txt
├── LICENSE
└── README.md
```

## Requirements

Python 3.8 or newer. No third-party packages.

## Usage

```bash
git clone https://github.com/<your-username>/expense-tracker.git
cd expense-tracker

python main.py add 250 Food -d "Lunch" --date 2026-07-01
python main.py add 1500 Books -d "Python book" --date 2026-07-05
python main.py add 300 Food -d "Dinner" --date 2026-07-12
python main.py add 120 Travel -d "Bus pass" --date 2026-07-15

python main.py list
python main.py list -c food -m 2026-07
python main.py summary
python main.py export expenses.csv
python main.py delete 3
python main.py --help
```

Example output:

```
ID   Date       Category         Amount  Description
--------------------------------------------------------
4    2026-07-15 Travel           120.00  Bus pass
3    2026-07-12 Food             300.00  Dinner
2    2026-07-05 Books           1500.00  Python book
1    2026-07-01 Food             250.00  Lunch
--------------------------------------------------------
Total                           2170.00

Books           1500.00  ##############################
Food             550.00  ###########
Travel           120.00  ##
Total           2170.00
```

The data file is `expenses.json` in the current folder. Use `--file path.json` or the
`EXPENSE_TRACKER_FILE` environment variable to choose a different file.

## Running the tests

```bash
python -m unittest discover -v
```

## Possible improvements

- Monthly budgets with warnings
- Charts using Matplotlib
- Storing data in SQLite instead of JSON

## License

Released under the MIT License - see [LICENSE](LICENSE).
