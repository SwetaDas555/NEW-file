# File Integrity Checker

## Introduction

The File Integrity Checker is a Python-based cybersecurity project designed to help identify changes made to files. It uses the SHA-256 hashing algorithm to create a baseline of selected files and checks whether their contents have changed over time.

File integrity is an important part of cybersecurity because unexpected changes to files may indicate unauthorized access, tampering, malware activity, or accidental modifications. This project provides a simple way to detect these changes and understand how file integrity monitoring works in practice.

## Project Objectives

The main objective of this project is to develop a simple tool that can check the integrity of files and report any differences from their original state.

The project aims to:

- Calculate SHA-256 hashes for selected files.
- Create a baseline for future integrity checks.
- Detect modified, missing, and newly added files.
- Allow the baseline to be updated when changes are legitimate.
- Provide practical experience with Python and cybersecurity concepts.
- Support basic digital forensics and security monitoring exercises.

## Technologies Used

The project uses Python 3 and its built-in libraries to calculate file hashes, store baseline information in JSON format, and provide a command-line interface. SHA-256 is used to compare files without relying on their names or file extensions alone.

The tool can be used on Kali Linux and other systems with Python installed.

## Project Structure

```text
integrity-checker/
├── integrity_check.py
├── README.md
├── LICENSE
├── .gitignore
├── tests/
│   └── test_integrity_check.py
├── samples/
│   ├── app.log
│   └── auth.log
└── reports/
    └── .gitkeep
```

## Getting Started

First, clone the repository and move into the project directory:

```bash
git clone https://github.com/SwetaDas555/NEW-file.git
cd NEW-file
```

Check that Python is installed:

```bash
python3 --version
```

The main program uses Python's standard library, so additional packages are not required to run it.

## How to Use the Tool

### Create a baseline

Run the following command to record the current state of the sample files:

```bash
python3 integrity_check.py init samples
```

The program calculates the SHA-256 hashes and saves them as a reference for later checks.

### Check file integrity

To compare the current files with the saved baseline, run:

```bash
python3 integrity_check.py check samples
```

The tool reports changes it detects, including modified or missing files and files that were not part of the original baseline.

### Test change detection

To test the tool, add a line to one of the sample files:

```bash
echo "Test modification" >> samples/app.log
```

Run the integrity check again:

```bash
python3 integrity_check.py check samples
```

The changed file should be reported because its SHA-256 hash no longer matches the saved baseline.

### Update the baseline

If you have checked a change and confirmed that it is legitimate, you can update the baseline for that file:

```bash
python3 integrity_check.py update samples/app.log
```

It is important to verify changes before updating the baseline. Otherwise, an unauthorized modification could become part of the new reference state.

## How the Project Works

The tool follows a straightforward process. It reads the selected files, calculates their SHA-256 hashes, and saves those values in a baseline. When an integrity check is performed, it calculates the hashes again and compares them with the stored values.

If a file's content changes, its hash will normally change as well. This allows the tool to identify differences without needing to understand the contents of each file.

## Practical Applications

This project demonstrates how file integrity checking can support cybersecurity activities such as:

- Identifying unexpected file modifications.
- Learning basic digital forensics techniques.
- Supporting incident-response investigations.
- Checking the integrity of log files and configuration files.
- Understanding cryptographic hashing and evidence verification.

## Testing

Unit tests are included in the `tests/` directory to help check the program's behaviour. If `pytest` is installed, the tests can be run with:

```bash
python3 -m pytest -v
```

The test framework is only needed for running the tests, not for normal use of the tool.

## Limitations

This tool identifies changes to files, but it cannot determine whether a change was malicious or explain who made it. It also does not provide continuous, real-time monitoring.

The stored baseline must be protected. If someone can modify both a monitored file and its baseline, the tool may not detect the original tampering. For more reliable monitoring, the baseline should be kept in a protected location or backed up separately.

## Future Improvements

The project could be extended with real-time monitoring, automated alerts, HTML or CSV reports, a graphical interface, and stronger protection for baseline data. These improvements would make it more useful for practical security monitoring and investigation.

## Author

**Sweta Kumari Das**

Cybersecurity and Digital Forensics Student

GitHub: https://github.com/SwetaDas555

## License

This project is provided under the MIT License. Refer to the `LICENSE` file for details.

## Disclaimer

This project was developed for educational purposes and defensive cybersecurity practice. It should only be used on files and systems that you own or are authorized to examine.
