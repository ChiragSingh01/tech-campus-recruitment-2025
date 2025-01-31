# Log Extraction Scripts

## Overview

This repository contains two scripts for extracting logs from a file based on a specific date. The logs are filtered by matching lines that start with the specified date, and the results are saved to an output file.

- **Python Code** uses the `multiprocessing` module to handle large log files efficiently.
- **JavaScript Code (Node.js)** uses asynchronous processing with `readline` and `fs` modules for non-blocking I/O operations.

# Python Log Extraction Script

## Overview

This Python script extracts logs from a log file based on a specific date. It uses the `multiprocessing` module to process large log files more efficiently by parallelizing the task.

---

## How the Python Code Works

### Imports
- **os** and **sys**: These modules are used to manage file paths and handle system arguments for the script.
- **multiprocessing.Pool**: This module is used to parallelize the log extraction task by processing multiple dates concurrently, improving efficiency when handling large log files.

### Functions

#### `extract_logs(date, input_file, output_file)`
- This function handles reading the input log file line by line.
- It checks if a line starts with the provided date and writes the matching lines to the output file.

#### `process_logs(date)`
- This function serves as the entry point for processing logs for a specific date.
- It prepares the file paths and calls the `extract_logs` function to perform the extraction.

### Main Execution
- The `__main__` block ensures that the script only runs when executed directly (not when imported as a module).
- It checks if the date is passed correctly as a command-line argument in the `YYYY-MM-DD` format.
- The script utilizes `multiprocessing.Pool` to parallelize the log extraction process. You can adjust the pool size (in this case, 32 processes) depending on your machine's capabilities.

### Key Points
- The log file is read line by line.
- If a line starts with the provided date, it is written to the output file.
- If the date format is incorrect, or if the file is missing, the script will display appropriate error messages.


# JavaScript Log Extraction Script

## Overview

This Node.js script is designed to extract logs from a log file based on a specific date. It is written in an asynchronous style, making it well-suited for high-performance I/O tasks, ensuring that large files can be processed efficiently without blocking the event loop.

---

## How the JavaScript Code Works

### Imports
- **fs**: Used for reading from and writing to files.
- **readline**: This module handles reading the log file line by line asynchronously.
- **path**: Used for managing file paths and ensuring the correct output file location.

### Function

#### `extractLogs(date)`
- This function reads the log file line by line using the `readline` module.
- For each line, it checks if the line starts with the given date.
- If the line matches, it writes the line to the output file.

### Main Execution
- The script expects the date to be passed as a command-line argument in the `YYYY-MM-DD` format.
- It verifies the date format using a regular expression (`/^\d{4}-\d{2}-\d{2}$/`).
- The `readline` module is used to read the log file asynchronously, ensuring that the event loop is not blocked, even when processing large files.

### Key Points
- The log file is processed asynchronously using `readline` and `fs.createReadStream`.
- If a line starts with the specified date, it is written to the output file using `fs.createWriteStream`.
- The script will output an error if the date format is incorrect or if there are issues with file paths, similar to the Python version.

# Comparison of Python and JavaScript Code

| Feature              | Python Code                                              | JavaScript Code (Node.js)                                   |
|----------------------|----------------------------------------------------------|------------------------------------------------------------|
| **Language**         | Python                                                   | JavaScript (Node.js)                                       |
| **Concurrency Model**| Uses multiprocessing for parallel processing.            | Uses asynchronous programming with async/await and the readline module for efficient I/O. |
| **File I/O**         | Reads the entire file in memory at once and processes it line by line. Writes results to a file. | Reads the file line by line asynchronously using readline and fs.createReadStream. Writes results asynchronously using fs.createWriteStream. |
| **Error Handling**   | Catches FileNotFoundError and other generic exceptions.  | Catches asynchronous errors using try/catch and outputs errors in the console. |
| **Parallelism**      | Can process multiple dates in parallel with multiprocessing.Pool. | No explicit parallelism in the code; processes one date at a time asynchronously. |
| **File Handling**    | Uses open for reading and writing, with buffering for performance. | Uses fs.createReadStream and fs.createWriteStream for efficient file handling. |
| **Date Validation**  | Checks the date format using sys.argv and ensures it is in YYYY-MM-DD format. | Uses a regular expression (/^\d{4}-\d{2}-\d{2}$/) to validate the date format. |
| **Output Location**  | Ensures the output directory exists using os.makedirs(). | Ensures the output directory exists using fs.mkdirSync(). |
| **Command-Line Arguments** | Takes the date as an argument via sys.argv. | Takes the date as an argument via process.argv. |

---

## Python Code

### Requirements
- Python 3.x
- `multiprocessing` (Python standard library)

### How to Use
1. Install Python 3.x.
2. Ensure the log file is located at the specified path.
3. Run the script with a date argument in `YYYY-MM-DD` format:
   ```bash
   python extract_logs.py YYYY-MM-DD
