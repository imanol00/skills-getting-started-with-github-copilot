# Test Suite for Mergington High School API

This directory contains comprehensive tests for the FastAPI application using pytest.

## Test Structure

- `test_api.py`: Main test file containing all API endpoint tests

## Test Coverage

### Test Classes

1. **TestRootEndpoint** - Tests for the root endpoint
   - Verifies redirect to static/index.html

2. **TestGetActivities** - Tests for GET /activities
   - Returns 200 status code
   - Returns proper dictionary structure
   - Contains expected fields (description, schedule, participants, max_participants)
   - Includes specific activity verification

3. **TestSignupForActivity** - Tests for POST /activities/{activity_name}/signup
   - Successful signup for existing activities
   - Participant addition verification
   - 404 error for non-existent activities
   - 400 error for duplicate signups
   - URL encoding handling
   - Special characters in email support

4. **TestUnregisterFromActivity** - Tests for DELETE /activities/{activity_name}/unregister
   - Successful unregistration of existing participants
   - Participant removal verification
   - 404 error for non-existent activities
   - 400 error for non-registered participants
   - URL encoding handling

5. **TestIntegration** - End-to-end workflow tests
   - Complete signup and unregister workflow
   - Multiple activity signups
   - Participant count accuracy

## Running the Tests

### Run all tests
```bash
pytest tests/
```

### Run with verbose output
```bash
pytest tests/ -v
```

### Run with coverage
```bash
pytest tests/ --cov=src --cov-report=html
```

### Run specific test class
```bash
pytest tests/test_api.py::TestSignupForActivity -v
```

### Run specific test
```bash
pytest tests/test_api.py::TestSignupForActivity::test_signup_for_existing_activity_success -v
```

## Test Fixtures

- `client`: Creates a TestClient for the FastAPI app
- `reset_activities`: Automatically resets activity data before each test to ensure test isolation

## Dependencies

The following packages are required (added to requirements.txt):
- pytest
- pytest-asyncio
- httpx

## Test Results

✅ All 19 tests passing
- 1 Root endpoint test
- 4 Get activities tests
- 6 Signup tests
- 5 Unregister tests
- 3 Integration tests

## Best Practices Used

1. **Test Isolation**: Each test resets the activities data to a known state
2. **Clear Test Names**: Descriptive test names that explain what is being tested
3. **Organized Structure**: Tests grouped by functionality using classes
4. **Edge Cases**: Tests cover error conditions, special characters, and URL encoding
5. **Integration Tests**: End-to-end workflows to verify complete user journeys
6. **Assertions**: Clear assertions with meaningful error messages
