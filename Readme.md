# Log File Extraction Tool

This repository contains a tool to efficiently extract logs from a large log file. The tool reads a log file line by line and extracts entries for a specific date, saving the results to an output file. This is useful for quickly filtering logs for specific dates in large log files. I have used two languages JavaScript and Python.

## Features of JavaScript Code

- Extract logs from a specific date.
- Efficient handling of large log files by reading them line by line.
- Saves the extracted logs into an output text file.
- Supports flexible paths for both input and output.

## Prerequisites

- Node.js (>=12.x) must be installed on your machine to run the script.
- A log file in a specific format is required. Each log entry should start with a timestamp (YYYY-MM-DD), followed by the log level, and the log message.

## Features of Pyhton Code

- Extract logs from a specific date.
- Efficient handling of large log files by reading them line by line.
- Saves the extracted logs into an output text file.
- Supports flexible paths for both input and output.

## Prerequisites

- Python 3.x must be installed on your machine.
- A log file in a specific format is required. Each log entry should start with a timestamp (YYYY-MM-DD), followed by the log level, and the log message.

## Main Differences Between JavaScript and Python Implementations

| Feature                          | JavaScript (Node.js)                                      | Python                                                |
|----------------------------------|-----------------------------------------------------------|-------------------------------------------------------|
| **File Paths Handling**          | Uses `path.join` and `fs` for file handling               | Uses `os.path.join` and `os` for file handling        |
| **File Reading**                 | Uses streams (`fs.createReadStream`, `readline.createInterface`) | Uses `open()` with manual iteration through lines    |
| **Buffering**                    | No explicit buffering used                                | Uses buffered writing (`buffering=1024*1024`)         |
| **Directory Creation**           | `fs.mkdirSync`                                            | `os.makedirs()`                                        |
| **Command-Line Arguments**       | Direct access to `process.argv`                           | Access via `sys.argv` with additional format validation |
| **Error Handling**               | Uses `try-catch`                                          | Uses `try-except`                                      |
| **Logging and Output**           | Uses `console.log()` for output                           | Uses `print()` for output                             |
| **Streaming vs Direct File Handling** | Works with streams for reading and writing               | Direct file reading and writing in Python code        |

### Explanation
This table summarizes the key differences between the JavaScript (Node.js) and Python versions of the log extraction script. Each version is optimized for its respective language environment, with Node.js leveraging streams for better performance in a non-blocking I/O model, while Python handles large files with buffering to optimize memory usage.


## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/Extract-Logfile.git
