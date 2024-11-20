# AWS IAM Policy Management Test Framework

This project provides a test automation framework to validate the creation, validation, and limitations of AWS Identity and Access Management (IAM) policies. It includes both policy definitions and automated tests to ensure proper behavior and limits when working with IAM policies.

## Purpose

This framework:
1. Defines and validates three different IAM policies.
2. Tests the enforcement of a policy creation limit.
3. Implements error handling and assertions to validate policy functionality.
4. Leverages an Excel sheet for test case management and results recording.

## Features

### Part 1: IAM Policy Definitions
The following IAM policies are defined:
1. **Policy to Restrict Policy Count**: Restricts the number of IAM policies to 4.
2. **Read-Only Access to S3**: Grants read-only access to S3 buckets.
3. **Full Access to EC2**: Grants full access to EC2 instances.
4. **Read-Write Access to DynamoDB**: Grants read-write access to DynamoDB tables.

### Part 2: Test Suite
The test suite:
- **Validates Policy Creation**:
  - Allows the creation of up to 3 policies (positive test).
  - Fails gracefully when attempting to create a 4th policy (negative test).
- **Policy Content Verification**:
  - Confirms that created policies have the correct attributes and contents.
- **Cleanup**:
  - Removes any created policies after tests to ensure a clean state.
- **Error Handling**:
  - Implements robust error handling with meaningful assertions and messages.
- **Reporting**:
  - Records test results dynamically in an Excel file.

### Test Case Management with Excel
1. **Reading Test Cases**:
   - The framework reads test case details from an Excel file.
   - Each row in the file represents a test case, including inputs such as policy details, expected outcomes, and test descriptions.
2. **Writing Results**:
   - After executing each test, the framework writes the test results (e.g., **Pass**, **Fail**, or **Error**) back into the Excel sheet.
   - Additional details such as failure reasons or logs are appended for failed cases.
3. **Dynamic Updates**:
   - The framework ensures that test case status and execution logs are kept up-to-date for real-time validation and reporting.

### Reporting
- Test results are saved in the updated Excel sheet for future reference.
- The framework generates a summary of test outcomes, highlighting successful and failed cases, along with reasons for failure.

## Technical Requirements

- **Python**: Requires Python 3.11 or higher.
- **AWS SDK**: Utilizes `boto3` for interacting with AWS IAM services.
- **Excel Management**: Uses `openpyxl` for reading and writing to Excel files.
- **Testing Framework**: Built with Python's standard testing libraries and extensions.
- **Dependencies**: A `requirements.txt` file is provided for setting up dependencies.

## Setup Instructions

### Prerequisites
1. Install Python 3.11+.
2. Configure AWS credentials with sufficient IAM privileges to create, verify, and delete policies.

### Installation
1. Clone the repository:
   ```bash
   git clone <repository_url>
   cd <repository_directory>
