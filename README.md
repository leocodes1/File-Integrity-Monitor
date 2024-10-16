# File-Integrity-Monitor

File Integrity Monitor
This File Integrity Monitor is a Python application designed to detect changes in files within a specified directory. Utilizing the hashlib library, it computes SHA-256 hashes for each file, creating a baseline for comparison. The application monitors the directory for new, modified, or deleted files, providing real-time feedback on any changes detected.

Features
* Create a baseline of file hashes to track changes
* Monitor a specified directory for new, modified, or deleted files
* Store baseline data in a JSON file for easy reference
* User-friendly command-line interface for interactions

Usage
* Run the script and choose options to create a baseline or monitor for changes.
* Enter the directory you want to monitor when prompted.
