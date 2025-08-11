# SonarQubeTesting Project - Test Plan

## What We Test

### API Testing
- **Authentication:** Login, logout, invalid credentials.
- **Health:** SonarQube system health endpoint.
- **Projects:** Create, search, update, delete projects; error handling for non-existent projects.

### UI Testing
- **Login/Logout:** User authentication via the web interface.
- **Project Management:** Create and delete projects through the UI.
- **Navigation:** Page titles, visibility of key UI elements, and workflow navigation.

## How We Test (Strategy)
- **Automated Testing:**
  - API tests use Python `requests` and `pytest` for endpoint validation and error handling.
  - UI tests use Selenium WebDriver (with Page Object Model) and `pytest` for browser-based workflow validation.
- **Integration:**
  - Tests are run against a live SonarQube instance (local or remote).
  - UI tests simulate real user actions; API tests validate backend logic and error responses.
- **Continuous Integration:**
  - Tests are executed automatically on every pull request via GitHub Actions.
- **Justification:**
  - SonarQube is a web-based platform with REST APIs and a rich UI, so both API and UI testing are required for full coverage.

## Success Criteria
- All critical API and UI workflows pass without errors.
- All assertions in tests are met (e.g., correct status codes, expected UI elements, success messages).
- No unhandled exceptions or Selenium/requests errors.

## Test Environment
- **SonarQube Server:**
  - Remote: BASE_URL
  - Local: `http://localhost:9000` (for local runs)
- **Python:** 3.12
- **Browser:** Google Chrome (latest stable)
- **Driver:** ChromeDriver (matching Chrome version)
- **CI:** GitHub Actions (Ubuntu runners)

## Test Data
- **API:**
  - Valid and invalid credentials for authentication.
  - Sample project names and keys (e.g., `MyProject`, `my_project`).
  - Edge cases: non-existent projects, invalid keys.
- **UI:**
  - Admin credentials for login.
  - Project names/keys for creation and deletion.

## Reporting Results
- **Local:**
  - Pytest output in terminal (verbose mode).
- **CI:**
  - GitHub Actions job summary.
  - Coverage uploaded to Codecov.
  - Test failures and errors reported in PR checks.

---

This test plan ensures both API and UI functionality of SonarQube are validated in a repeatable, automated fashion, with results visible to all contributors.
