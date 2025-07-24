# Quantum Readiness Scanner

## Overview
This tool scans a directory for X.509 certificates, assesses the quantum vulnerability of their public keys (RSA/ECC) based on NIST thresholds, and generates a migration report recommending post-quantum algorithms.

## Setup
1. Create a Python virtual environment:
   bash
   python3 -m venv venv
   source venv/bin/activate  # or `.\venv\Scripts\activate.bat` on Windows CMD

## How to Use the Quantum Readiness Scanner
Basic Scan
To scan a folder containing certificate files (.pem, .crt, .cer, .der), use the following command:

python scanner.py path/to/folder -o report.md
path/to/folder: Replace with the path to the folder containing your certificate files

-o report.md: This is the output file where the scan results will be saved in Markdown format

Example:

python scanner.py test_certs -o test_report.md
This will create a file called test_report.md with the scan results.

How to Test a Real Website Certificate
If you want to test a certificate from a real website (e.g. https://example.com), follow these steps:

Open Google Chrome

Visit the website (e.g. https://example.com)

Click the padlock icon in the address bar

Click "Connection is secure" or "Certificate (Valid)"

In the certificate window, go to the Details tab and click "Copy to File..."

Choose Base-64 encoded X.509 (.CER) as the export format

Save the file into your project directory inside a folder named manual_certs, and name it something like site.cer

Once the certificate is saved:

python scanner.py manual_certs -o manual_report.md
Then open manual_report.md in your text editor to view the results.

Example Output
Quantum Readiness Scanner Report

manual_certs/site.cer
- Algorithm: RSA-2048
- Risk Level: High
- Recommended PQC: Kyber-1024, FrodoKEM-976-AES
