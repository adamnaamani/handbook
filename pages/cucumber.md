# Cucumber

## Table of Contents
1. [Setup](#setup)
1. [Features](#features)
1. [Testing Behaviour](#testing-behaviour)
1. [World](#world)

## Setup
```
brew cask install chromedriver
brew cask upgrade chromedriver
```

## Features
```bash
cucumber features/feature/name.feature
```

## Testing Behaviour
```
@chrome
```

## World
In Ruby, Cucumber runs scenarios in a `World`. By default, the `World` is an instance of `Object`.
  ```ruby
  World()
  ```
