# Ruby on Rails

## Table of Contents
[Statistics](#statistics)  
[Debugging](#debugging)  
[Namespaces](#namespaces)  
[Migrations](#migrations)  
[Associations](#associations)  
[Methods](#methods)  
[Lambda](#lambda)  
[Arguments](#arguments)
[Heredoc](#heredoc)
[Attributes](#attributes)  
[Interpolation](#interpolation)
[Navigators](#navigators)
[Store](#store)  
[Internationalization](#internationalization)  
[Validations](#validations)  

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