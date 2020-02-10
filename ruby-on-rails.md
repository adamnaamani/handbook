# Ruby on Rails

## Table of Contents


## Statistics
`rails stats`

## Migrations
### Strong Migrations
```ruby
disable_ddl_transaction!

safety_assured { add_index :properties, :pid, algorithm: :concurrently }
```

## Associations
### Polymorphic
* Where an ActiveRecord model can potentially belong to more than one other kind of model record. The single instance of your car belongs to you, a person, whereas other cars may individually belong to a car lot, a business.
  ```ruby
  belongs_to :listable, polymorphic: true
  ```

### Building
`.build`

## Attributes
### Assigning
`.assign_attributes`

### Virtual
Virtual Attribute or “setter” method:
```ruby
def foo=(x)
```

## Store
`store_accessor`

## Internationalization
```ruby
I18n.t('...')
```