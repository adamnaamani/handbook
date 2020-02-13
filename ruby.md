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
  
  Makes it so an array can't be modified.
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
  (lambda do |params|
  ...
  end)
  ```

## Pry
  ```ruby
  binding.pry
  ```

## Heredoc
  ```ruby
  <<-SQL
    SELECT * FROM properties
  SQL
  ```
  ```ruby
  <<~SQL
    SELECT * FROM properties
  SQL
  ```

## Interpolation
* Non-interpolated Array of symbols, separated by whitespace.
  ```ruby
  %i[param1 param2]
  ```
* Interpolated Array of symbols, separated by whitespace.
  ```ruby
  %I[] 
  ```

## Navigators
* Safe navigator
  ```ruby
  object&.property
  ```

## Arguments
* Keyword arguments: Vary the order of arguments with keywords.
  ```ruby
  def method(pid:, status:, city: 'Vancouver'); end

  method(status: 'Active', pid: '123-456-789')
  ```
* Array splat operator:
  ```ruby
  def method(*array); end
  ```
* Hash splat operator:
  ```ruby
  def method(**hash); end
  ```
