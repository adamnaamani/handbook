# Testing

## Table of Contents
1. [Rspec](/rspec.md)
2. [Cucumber](/cucumber.md)
3. [Jest](/jest.md)

* Unit tests: test small pieces of app in isolated environment, mocking the external dependencies.
* End-to-end tests: whole system should work when everything is connected.
* Integration tests: given entry point, should validate how components of a module or feature interact.

Properly factored code should be small and concise. Code should typically depend less on the state of the data in relation to the database and more on its state in relation to other objects.

Four phase sequence:
1. Setup
2. Exercise
3. Verify
4. Teardown