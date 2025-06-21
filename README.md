# Hybrid Automation Framework for Web Application

## Overview
This is a Hybrid Automation Framework designed for web application testing using Selenium WebDriver, TestNG, Java, and Apache POI.  
The framework combines both **data-driven** and **keyword-driven** approaches, enabling flexible, maintainable, and scalable test automation.  
It supports modular test case execution, dynamic data handling from Excel, and generates clear execution reports.

## Key Features
- **Hybrid Design:** Combines data-driven and keyword-driven testing for maximum flexibility.
- **Modular Structure:** Separate layers for test cases, business logic, and utilities.
- **Excel Integration:** Test data, test steps, and execution flow are managed via Excel files.
- **Reusable Components:** Common actions (click, type, dropdown, validation, etc.) are implemented as reusable methods.
- **Dynamic Execution:** Test cases can be enabled/disabled via Excel (Y/N flag).
- **Automated Reporting:** Generates colored pass/fail/blocked status in Excel and detailed HTML reports.
- **Cross-browser Support:** Easily switch between Chrome and Firefox via properties file.

## Technologies Used
- Java
- Selenium WebDriver
- TestNG
- Apache POI (for Excel operations)
- ExtentReports (for HTML reporting)
- Maven (dependency management)

## Project Structure
project-root/
│
├── src/
│ ├── commonFunctions/ # Core reusable functions (keywords)
│ ├── driverFactory/ # TestNG runner classes
│ ├── utilities/ # Excel utilities
│ └── PropertyFiles/ # Configurations (Environment.properties)
│
├── FileInput/ # Input Excel files (test data, test steps)
├── FileOutput/ # Output Excel files (results)
├── CaptureData/ # Captured runtime data (e.g., stocknum.txt)
├── test-output/ # TestNG/ExtentReports output
├── pom.xml # Maven dependencies
└── README.md

## How It Works
1. **Test case execution is controlled via Excel:**  
   - The `MasterTestCases` sheet lists all modules and their execution status (Y/N).
   - Each module has its own sheet with step-by-step keywords and data.
2. **Driver script reads Excel:**  
   - For each test case marked "Y," the framework executes the steps by matching keywords to functions in `FunctionLibrary`.
   - Status ("Pass"/"Fail"/"Blocked") is written back to Excel and color-coded.
3. **Reports are generated:**  
   - HTML and Excel reports are created for each run.

## Sample MasterTestCases Excel Sheet
| TCID  | ModuleName       | ExecutionStatus | Status  |
|-------|------------------|----------------|---------|
| TC001 | AplicationLogin  | Y              |         |
| TC002 | Stockitems       | Y              |         |
| TC003 | Suppliers        | N              |         |
| TC004 | Costumers        | N              |         |

- Only modules with "Y" in ExecutionStatus will run.  
- Status will be updated automatically after execution.

## How to Run
1. **Clone this repository** and open in your IDE.
2. **Install dependencies:**  
   `mvn clean install`
3. **Update configurations:**  
   - Set browser and URL in `PropertyFiles/Environment.properties`.
   - Place your test data in `FileInput/DataEngine.xlsx`.
4. **Run the tests:**  
   - Use TestNG runner class (`AppTest.java`) or run via TestNG XML suite.
5. **Check results:**  
   - Output Excel and HTML reports will be available in `FileOutput/` and `test-output/`.

## Disclaimer
This project was developed as part of a training program and is intended for educational and demonstration purposes only.
