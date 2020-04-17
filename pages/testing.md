# Testing

Properly factored code should be small and concise. Code should typically depend less on the state of the data in relation to the database and more on its state in relation to other objects.

## Table of Contents
1. [Phases](#phases)
1. [Types](#types)
   1. [Unit Tests](#unit-tests)
   1. [End-to-end Tests](#end-to-end-tests)
   1. [Integration Tests](#integration-tests)
1. [Libraries](#libraries)

## Phases
Four phase sequence:
1. Setup
1. Exercise
1. Verify
1. Teardown

## Types
### Unit Tests  
Test small pieces of app in isolated environment, mocking the external dependencies.

### End-to-end Tests  
Whole system should work when everything is connected.

### Integration Tests  
Given entry point, should validate how components of a module or feature interact.

## Libraries
1. [Rspec](/pages/rspec.md)
1. [Cucumber](/pages/cucumber.md)
1. [Jest](/pages/jest.md)
