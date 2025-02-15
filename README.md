# py-sreport

# SLURM Job Report

## Table of Contents

- [Description](#description)
- [Installation](#installation)
- [Usage](#usage)
- [Options](#options)
- [Functions](#functions)
- [Examples](#examples)
- [License](https://github.com/ricardojacomini/py-sreport?tab=GPL-2.0-1-ov-file)

## Description

The py-sreport script generates a detailed report on SLURM account and resource usage. It retrieves data from SLURM's accounting system using various commands and formats the output for readability. Acting as a wrapper for the sreport command, it provides a user-friendly interface to access scheduler database records, which are stored on disk and periodically updated by the SLURM controller.

**Note**: This open-source script can be freely used and modified. We welcome your suggestions or feedback and look forward to incorporating your improvements.


## Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/ricardojacomini/py-sreport.git
    ```
2. Navigate to the project directory:
    ```sh
    cd py-sreport
    ```
3. Ensure you have Python 3 installed. You can check your Python version with:
    ```sh
    python3 --version
    ```

## Usage

To run the script, use the following command:
```sh
./py-sreport [options]
```

## Options

- `-u`, `--user`: Specify a user to check usage.
- `-p`, `--pi`: Specify a PI to check usage.
- `--hide-zero`: Hide users with 0.0 used core-hours.
- `--start-date`: Specify the start date (YYYY-MM-DD).
- `--end-date`: Specify the end date (YYYY-MM-DD).
- `--usage`: Show a column of usage data as a percentage of the allocation.

**Note:** If `--start-date` is passed as an argument but not `--end-date`, then the script will set the current date and time as the end date.


## Functions

- `get_current_quarter_dates()`: Returns the start and end dates of the current quarter.
- `get_user()`: Returns the current logged-in user.
- `slurm_command(command)`: Executes a SLURM command and returns the output.
- `get_allocation(account)`: Retrieves the allocation for a given account.
- `get_accounts(user, PI)`: Retrieves the accounts associated with a user or PI.
- `AccountUtilization(account, start_date, end_date)`: Retrieves the account utilization data for a given account and date range.
- `format_output(usage_data, allocation, account, used, usage, usage_column, space)`: Formats the output for the report.
- `account_data(accounts, hide_zero, start_date, end_date, usage_column)`: Generates and prints the account usage report.
- `main()`: Parses command-line arguments and generates the report.

## Examples

To generate a report for a specific user:
```sh
./py-sreport -u username
```

To generate a report for a PI:
```sh
./py-sreport -p pi_name
```

To generate a report with hidden zero usage:
```sh
./py-sreport --hide-zero
```

To generate a report with a specific date range:
```sh
./py-sreport --start-date 2025-01-15 --end-date 2025-02-31
```

**Note**: For optimal use of `py-sreport`, adding the directory containing the script to your system's PATH is recommended. This will allow you to run the script from anywhere without having to specify the full path. Once you've added the directory to your PATH, you can run the script simply by typing `py-sreport` in your terminal or command prompt.
