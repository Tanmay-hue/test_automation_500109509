# Backend API Test Automation 🚀

This project offers a robust framework for API testing on a FastAPI backend. It leverages pytest for automated testing, integrates with GitHub Actions for CI/CD, and includes performance testing and comprehensive reporting tools.

---

## Project Overview 🛠️

### What It Does

- **FastAPI Backend**: Implements a REST API with endpoints for arithmetic operations, complete with validation and error handling.
- **Automated Testing**: Uses pytest with parameterized tests, covers edge cases, and integrates Allure reporting.
- **Performance Testing**: Employs Locust to simulate concurrent users, measuring response times and system performance.
- **CI/CD Integration**: Automated workflows using GitHub Actions streamline testing, reporting, and deployment.

### Troubleshooting & Resolutions

During initial GitHub Actions runs, several issues were identified and resolved:

1. **Workflow File Errors**
   - **Issue**: "Invalid workflow file: .github/workflows/TestAutomation.yml#L18"
   - **Resolution**: Split multiple `run` commands into separate steps and corrected YAML formatting.

2. **Outdated Action Version**
   - **Issue**: "Missing download info for actions/upload-artifact@v2"
   - **Resolution**: Upgraded to `actions/upload-artifact@v4`.

3. **Test Execution Failures**
   - **Issue**: "Process completed with exit code 2"
   - **Resolution**: Added missing dependencies (`httpx`, `starlette`) and fixed import issues.

4. **Artifact Directory Not Found**
   - **Issue**: "No files were found with the provided path: ./allure-results"
   - **Resolution**: Introduced a step to create the `allure-results` directory before running tests.

---

## Key Components

### 1. API Server (apiserver.py) 🌐

- Developed using FastAPI to provide REST endpoints.
- Handles arithmetic operations with robust input validation.
- Auto-generates API documentation.

### 2. Test Suite (automation_test_pytest.py) 🧪

- Contains parameterized and edge case tests.
- Validates error handling and includes performance benchmarks.
- Integrates with Allure for detailed reporting.

### 3. Performance Testing (performance_test.py) 🚀

- Utilizes Locust to simulate concurrent user traffic.
- Monitors response times and performance metrics.
- Provides insights into system behavior under load.

### 4. Configuration (config.py) ⚙️

- Manages environment-specific settings.
- Configures base URLs, timeouts, and test parameters.
- Enables flexible configuration for diverse deployment environments.

---

## Repository Layout 📂

```
.
├── apiserver.py              # FastAPI backend implementation
├── automation_test_pytest.py # Automated test suite
├── performance_test.py       # Load testing script with Locust
├── config.py                 # Configuration settings
├── requirements.txt          # List of project dependencies
└── .github/
    └── workflows/
        └── TestAutomation.yml  # GitHub Actions workflow configuration
```

---

## Getting Started 🚀

### Prerequisites

- **Python 3.10+**
- **pip** for installing packages
- **Git** for version control

### Installation Instructions

1. **Clone the Repository:**

   ```bash
   git clone <repository-url>
   cd <repository-name>
   ```

2. **Set Up a Virtual Environment:**

   ```bash
   python -m venv venv
   source venv/bin/activate  # Windows: venv\Scripts\activate
   ```

3. **Install Required Dependencies:**

   ```bash
   pip install -r requirements.txt
   ```

### Running the Application

- **Start the Server:**

  ```bash
  python apiserver.py
  ```

  The API server will be accessible at `http://localhost:8000`.

- **Execute Unit Tests with Coverage:**

  ```bash
  pytest automation_test_pytest.py -v --cov=apiserver --html=report.html
  ```

- **Run Performance Tests:**

  ```bash
  locust -f performance_test.py --host=http://localhost:8000
  ```

---

## Reporting & Documentation

- **Test Report Screenshot:**

  ![Test Report](https://github.com/Tanmay-hue/test_automation_500109509/blob/main/docs/test-report.png)

- **HTML Report**: Generated as `report.html` after running tests.
- **Allure Report**: Launch with `allure serve ./allure-results`.
- **Coverage Report**: Displayed in the terminal.

---

## CI/CD Pipeline Overview

The project utilizes GitHub Actions to automate the following tasks:

- **Triggering on push and pull requests**
- **Setting up the Python environment**
- **Installing dependencies and running tests**
- **Executing performance tests and load simulations**
- **Generating and uploading test reports**

---

## Test Scenarios

### Unit Tests

- Validates basic arithmetic operations.
- Covers edge cases (e.g., negatives, zero).
- Tests input validation and error handling.
- Checks response times.

### Performance Tests

- Simulates concurrent user load.
- Monitors response times under simulated traffic.
- Evaluates system performance and resource usage.

---

## Configuration Details

### Environment Variables

- **API_BASE_URL**: Default is `http://localhost:8000`
- **ENV**: Development, staging, or production setting.
- **TEST_TIMEOUT**: Maximum test duration in seconds.
- **PERFORMANCE_TEST_USERS**: Number of simulated concurrent users.

### Test Settings

- **Coverage Threshold**: 80% minimum.
- **Performance Test Duration**: 1 minute.
- **Concurrent Users**: 10, with a spawn rate of 1 user/second.

---

## API Documentation

Interactive API documentation is available at:

- **Swagger UI**: [http://localhost:8000/docs](http://localhost:8000/docs)
- **ReDoc**: [http://localhost:8000/redoc](http://localhost:8000/redoc)

---

## Logging & Monitoring

- **Execution Logs**: Detailed logs for test runs and performance metrics.
- **Error Tracking**: Integrated error monitoring.
- **Coverage Analysis**: Provided upon test completion.

---

## Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Push to your branch.
5. Open a Pull Request.

---

## Acknowledgments

- **FastAPI**: For providing the web framework.
- **pytest**: For the testing framework.
- **Locust**: For performance testing.
- **GitHub Actions**: For CI/CD automation.
- **Allure**: For detailed test reporting.

---

## Author

Tanmay Singh

---
