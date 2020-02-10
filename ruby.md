# Ruby

```ruby
```

## Table of Contents


## Namespacing
* Top level namespace:
  ```ruby
  ::Namespace::Service::Class.call()
  ```

## Methods
* `.freeze`
  ```ruby
  %w[one two three].freeze
  ```
* `.reload`

  Attributes are reloaded from the database, and caches busted, in particular the associations cache.
  ```ruby
  object.reload
  ```
* `.all?(*args)`
  
  Passes each element of the collection to the given block.  

## Lambda Functions
Anonymous function
```ruby
lambda { |params|
...
}
```

## Pry
  ```ruby
  binding.pry
  ```

## Heredoc
  ```
  <<-SQL
    SELECT * FROM properties
  SQL
  ```
  ```
  <<~SQL
    SELECT * FROM properties
  SQL
  ```

## Interpolation
* Non-interpolated Array of symbols, separated by whitespace
  ```ruby
  %i[param1 param2]
  ```
* Interpolated Array of symbols, separated by whitespace
  ```ruby
  %I[] 
  ```

## Navigators
* Safe navigator
  ```ruby
  object&.property
  ```

## Splat
* Array splat operator:
```ruby
def method(*array); end
```
* Hash splat operator:
```ruby
def method(**hash); end
```
