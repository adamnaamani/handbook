# Ruby on Rails

## Table of Contents
1. [Statistics](#statistics)  
1. [Debugging](#debugging)  
1. [Namespaces](#namespaces)  
1. [Migrations](#migrations)  
1. [Associations](#associations)  
1. [Methods](#methods)  
1. [Lambda](#lambda)  
1. [Arguments](#arguments)
1. [Heredoc](#heredoc)
1. [Attributes](#attributes)  
1. [Interpolation](#interpolation)
1. [Navigators](#navigators)
1. [Store](#store)  
1. [Internationalization](#internationalization)  
1. [Validations](#validations)  
1. [Errors](#errors)
1. [ActiveJob](#activejob)

## Statistics
`rails stats`

## Debugging
* Pry
  ```ruby
  binding.pry
  ```

## Namespaces
* Top level namespace:
  ```ruby
  ::Namespace::Service::Class.call()
  ```

## Migrations
* Strong Migrations
  ```ruby
  disable_ddl_transaction!

  safety_assured { add_index :properties, :pid, algorithm: :concurrently }
  ```

## Associations
### Polymorphic  
Where an ActiveRecord model can potentially belong to more than one other kind of model record. The single instance of your car belongs to you, a person, whereas other cars may individually belong to a car lot, a business.  
  ```ruby
  belongs_to :listable, polymorphic: true
  ```

### Building
Returns a new object of the collection type that has been instantiated with attributes and linked to this object, but have not yet been saved. You can pass an array of attributes hashes, this will return an array with the new objects.
```ruby
property.listings.build
#=> <Listing id: nil, full_address: nil, property_id: 1>
```

### Delegation
  Exposes contained objects' public methods as your own.
  * `:to` - Specifies the target object.
  * `:prefix` - Prefixes the new method with the target name or a custom prefix.
  * `:allow_nil` - If set to true, prevents a +Module::DelegationError+ from being raised.
  ```ruby
  delegate :full_address, to: :address
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
* `.presence`  
  Returns the receiver, or nil if it is not present.  
  ```ruby
  region = params[:country].presence || 'CA'
  ```  
* `.arity`  
  Returns an indication of the number of arguments accepted by a method.
  ```ruby
  class C
    def one; end
    def two(a); end
    def three(*a); end
    def four(a, b); end
  end
  
  c = C.new
  c.method(:one).arity   #=> 0
  c.method(:two).arity   #=> 1
  c.method(:three).arity #=> -1
  c.method(:four).arity  #=> 2
  ```
* `.changed?`  
  Returns true if any of the attributes has unsaved changes, false otherwise.
  ```ruby
  listing.property.changed?
  ```
* `.keep_if`  
  Deletes every element of self for which the given block evaluates to false. 
* `.is_a?`  
  Returns true if class is the class of object, or if class is one of the superclasses of object or modules included in object.
  ```ruby
  response.is_a?(Net::HTTPSuccess)
  ```
* `.clear`  
  Removes association from object.
  ```ruby
  listing.property.clear
  ```
* `.send`  
  Tests private methods
  ```ruby
  Listing.geocode.send
  ```
* `.clamp`  
  Can be used to keep a number within the range of min, max.
  ```ruby
  10.clamp(5, 20)
  #=> 10

  10.clamp(15, 20)
  #=> 15

  10.clamp(0, 5)
  #=> 5
  ```
* `.inject`  
  Combines all elements of enum by applying a binary operation, specified by a block or a symbol that names a method or operator.
  ```ruby
  [one, two, three].inject(:merge)
  ```
* `.abs`  
  Returns the absolute value of number.
  ```ruby
  -21.abs
  #=> 21
  ```
* `.any?`  
  Uses SQL count instead of loading each task, resulting in a faster, more performant result (from ~900ms down to ~100ms). However, what we actually want to know in this case is if there is at least one record in our scope. We don't really need to count all of the tasks, it should stop after finding the first one. So applying LIMIT would solve that for us.
  ```ruby
  property.listings.any?
  ```
* `.rjust`  
  If integer is greater than the length of string, returns a `new String` of length integer with string right justified and padded with `padstr`; otherwise, returns string.
  ```ruby
  "hello".rjust(4)            #=> "hello"
  "hello".rjust(20)           #=> "               hello"
  "hello".rjust(20, '1234')   #=> "123412341234123hello"
  ```
* `.tally`  
  Released in Rails 6. Counts the occurrence of each element.
  ```ruby
  ["a", "b", "c", "b"].tally
  #=> {"a"=>1, "b"=>2, "c"=>1}
  ```
* `.eager`  
  Released in Ruby 2.7. Generates a non-lazy enumerator from a lazy enumerator.  
  ```ruby
  a = %w(foo bar baz)
  e = a.lazy.map {|x| x.upcase }.map {|x| x + "!" }.eager
  p e.class               #=> Enumerator
  p e.map {|x| x + "?" }  #=> ["FOO!?", "BAR!?", "BAZ!?"]
  ```
* `.update_columns`  
  Updates the attributes directly in the database issuing an UPDATE SQL statement and sets them in the receiver. This is the fastest way to update attributes because it goes straight to the database, but take into account that in consequence the regular update procedures are totally bypassed.    
  ```ruby
  user.update_columns(last_request_at: Time.current)
  ```

## Services
Services have contracts that define their inputs and outputs. In many cases, a Create service should return the object, either persisted (without errors) or not (with errors, accessible for the service caller).    

## Lambda
Anonymous function
  ```ruby
  (lambda do |params|
  ...
  end)
  ```  

## Arguments
* Keyword arguments
  > Vary the order of arguments with keywords.
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
* Unused block arguments  
  > If it's necessary, use _ or _k as an argument name to indicate that it won't be used.
  ```ruby
    Import::ListingJob.perform_later(listing.symbolize_keys.reject { |_, v| v.blank? })
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

## Operators
* Pessimistic operator  
  > Highest-released gem version between a range.
  ```ruby
  ~> 1.0.0
  ```

## Attributes
* Assigning
  ```ruby
  .assign_attributes
  ```
* Setter method
  ```ruby
  def foo=(x); end
  ```
* Virtual
  ```ruby  
  attribute :attribute, Model  
  ```
* Dirty
  ```ruby
  _changed? 
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

## Store
`store_accessor`

## Internationalization
`en.yml` files written in YAML that store key value pairs for storing common message strings, etc.
* Translate
  ```ruby
  I18n.t('...')
  ```
* Localize
  ```ruby
  I18n.l('...')
  ```
* Variables  
  To create proper abstraction, the I18n gem ships with a feature called variable interpolation that allows you to use variables in translation definitions and pass the values for these variables to the translation method.
  ```yaml
  en:
    product_price: "$%{price}"
  ```
  ```ruby
  I18n.t('product_price', price: @product.price)
  ```

## Validations
You can check if a value is included in an array using the `inclusion:` helper. The `:in` option and its alias, `:within` show the set of acceptable values.
```ruby
validates :continent, inclusion: { in: %w(North America South America) }
```

## Errors
### Deadlock
A state in which each member of a group is waiting for another member, including itself, to take action, such as sending a message or more commonly releasing a lock.

## ActiveJob
I prefer [Sidekiq](https://sidekiq.org) for background processing:
> "_Need speed? Scale your app with Ruby's fastest job system, up to 20x faster than the competition!_"

#### [Embrace Concurrency](https://github.com/mperham/sidekiq/wiki/Best-Practices#3-embrace-concurrency)
> Sidekiq is designed for parallel execution so design your jobs so you can run lots of them in parallel. It has basic features for tuning concurrency (e.g. targeting a sidekiq process at a queue with a defined number of threads) but your system architecture is much simpler if you don't have such specialization.
```ruby
module Insert
  class PropertyJob < ApplicationJob
    queue_as :default

    def perform(city:, batch:)
      batch.each do |record|
        next if record.blank?

        Properties::Create.call(city, record.deep_symbolize_keys)
      end
    end
  end
end
```