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

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/Extract-Logfile.git
