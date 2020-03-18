# Rspec

## Table of Contents
1. [Components](#components)  
1. [Methods](#methods)  
1. [Conventions](#conventions)  
1. [Definitions](#definitions)  
1. [Factory Bot](#factory-bot)  
1. [Variables](#variables)
1. [Error Messages](#error-messages)
1. [Before](#before)
1. [Shared Example and Context](#shared-example-and-context)
1. [Defining Custom Objects](#defining-custom-objects)
1. [Described Class](#described-class)
1. [Subject](#subject)
1. [Testing](#testing)
1. [Matchers](#matchers)
1. [Compound Expectations](#compound-expectations)
1. [Mocks](#mocks)
1. [Expect vs. Allow](#expect-vs-allow)
1. [Receive](#receive)
1. [Matching Arguments](#matching-arguments)
1. [Traits](#traits)

## Components
* `rspec-core`: command-line program
* `rspec-expectations`: readable API to express expected outcomes
* `rspec-mocks`: tightly control environment
* `rspec-rails`: supports using rspec to test RoR applications

## Methods
* describe
* context
* it

## Conventions
In a describe block, it's conventional to use the method or class name as the description:
```ruby
# Method
describe '#method' do
  expect(subject).to eq(...)
end

# Class
describe '.class' do
  expect(subject).to eq(...)
end
```

## Definitions
* Specify: alias for “it".
* Hook: piece of code that runs automatically during a certain point in the test suite.

## FactoryBot
* Creates object and associations, persisted to database. Triggers validations.
  ```ruby
  create(:class)
  ```
* Won’t save object, but makes requests to database if factory has associations. Triggers validations only for associated objects.
  ```ruby
  build(:class)
  ```
* Doesn’t call database. Creates + assigns attributes, make it behave like instantiated object. Does not trigger validations.  
  ```ruby
  build_stubbed(:class)
  ```
* Returns a hash of attributes that can be used to build a Class instance.
  ```ruby
  attributes_for(:class)
  ```

## Variables
* let vs let!
  > The difference between let, and let! is that let! is called in an implicit before block. So the result is evaluated and cached before the it block.

## Error Messages
* Custom error message:
  ```ruby
  expect(…).to eq(…), “Error message” 
  ```

## Before
* Before example:
  ```ruby
  before(:example)
  ```
* Before context:
  ```ruby
  before(:context)
  ```

## Shared example and context
Both remove duplication across tests.
* Shared example:
  ```ruby
  RSpec.shared_example
  ```
  > The include_examples method injects predefined examples into an example group.
* Shared context
  ```ruby
  RSpec.shared_context
  ```
  > The include_context method injects context (i.e. before blocks, instance variables, helper methods, let variables) into an example group.

## Defining Custom Objects
Invoke the subject method and provide a Ruby block. The final evaluation of the block will be the value of subject whenever it's used in an example.
subject { "hello" }

## Described Class
`described_class` dynamically references the class being tested (the one passed as an argument to the top-level describe method). The advantage is that, if the class name changes, the rest of the spec does not have to change.

## Subject
* The subject equals an instance of the class under test.
* Subject is basically: `let(:subject) { Hash.new }` behind the scenes.
* One Liner Syntax: `it { is_expected.to eq(…) }`. It being subject.

## Testing
* You can use `puts` in test to see contents of object
* `binding.pry`

## Matchers
* to, not_to
* eq, eql (value, including same type), 
* equal, be (equal and be matcher, cares about object identity)
  ```ruby
  expect(10).to be > 5 (same Ruby operators)
  ```
  ```ruby
  describe 100 (functions as subject) do
    it { is_expected.to be > 90 }
  end
  ```
* Predicates (any Ruby predicate is available in RSpec)
  ```ruby
  even? -> be_even
  odd? -> be_odd
  empty? -> be_empty
  ```
* All matcher
  ```ruby
  expect([5, 7, 9, 13, 14]).to all(be_odd)
  expect([5, 7, 9]).to all(be < 10)
  ```
* Be matchers
  ```ruby
  falsy values — false, nil
  truthy values — everything else
  be_truthy
  be_falsey
  be_nil
  ```
* Change matcher
  ```ruby
  expect { subject.push(4) }.to change { subject.length }.by(1)
  ```
* Contain exactly matcher
  ```ruby
  expect(subject).to contain_exactly(1,2,3)
  it { is_expected.to contain_exactly(1,2,3) }
  ```
* Start with, End with matcher
  ```ruby
  start_with
  end_with
  ```
* Have attributes matcher
  ```ruby
  describe Person.new(‘Adam’) do
    it ‘checks for proper attributes’ do
      expect(subject).to have_attributes(name: ‘Adam’)
    end
  end

  it { is_expected.to have_attributes(name: ‘Adam’) 
  ```
* Include matcher
  ```ruby
  expect(subject).to include(‘Adam’)
  expect(subject).to include(:a, :b)
  expect(subject).to include(a: 2)
  it { is_expected.to include(‘Adam’) }
  ```
* Raise error matcher
  > List of Ruby errors: https://ruby-doc.org/core-2.5.1/Exception.html
  ```ruby
  expect { some_method }.to raise_error(NameError)
  
  class CustomError < StandardError; end
  
  expect { raise CustomError }.to raise_error(CustomError)
  ```
* Respond to matcher
  ```ruby
  expect(subject).to respond_to(:method, :method2, :method3).with(1).arguments
  it { is_expected.to respond_to(:method).with(1).arguments
  ```
* Satisfy matcher
  ```ruby
  it ‘is a palindrome’ do
    expect(subject).to satisfy { |value| value == value.reverse }
  end

  it ‘can accept a custom error message’ do
    expect(subject).to satisfy(‘be a palindrome’) do |value|
      value == value.reverse
    end
  end
  ```

## Compound expectations
* And
  ```ruby
  expect(subject).to be_odd.and be > 20
  it { is_expected.to be_odd.and be > 20 }
  expect(subject).to start_with(‘cat’).and end_with(‘pillar’)
  ```
* Or
  ```ruby
  expect(subject).to eq(:canada).or eq(:usa)
  ```

## Mocks
* double
  ```ruby
  let(:var) { double(‘string’, method: ‘test’) }
  ```
* Instance doubles
  ```ruby
  person = instance_double(Person)
  allow(person).to receive(:a).with(3, 10).and_return(‘Hello’)
  expect(person.a(3)).to eq(‘Hello’)
  ``` 
* Class doubles
  ```ruby
  class_double(Deck, build: [‘Ace’, ‘Queen’])
  class_double(Deck, build: [‘Ace’, ‘Queen’]).as_stubbed_const
  ```
* Spies
  ```ruby
  let(:animal) { spy(‘animal’) }
  ```

## Expect vs. Allow
* Expect
  ```ruby
  expect(var.method).to eq(‘test’)
  expect(calculator.add).to be_nil
  expect(calculator.add).to eq(15) 
  ```
* Allow
  ```ruby
  allow(var).to receive(:method) { ‘test’ }
  allow(stuntman).to receive_messages(fall_off_ladder: ‘Ouch’, light_on_fire: ‘True’)
  allow(calculator).to receive(:add)
  allow(calculator).to receive(:add).and_return(15)
  ```

## Receive 
* Counts
  ```ruby
  allow(var).to receive(:method).once
  allow(var).to receive(:method).exactly(1).times
  allow(var).to receive(:method).at_most(1).times
  allow(var).to receive(:method).at_least(2).times
  ```

## Matching arguments
  ```ruby
  allow(three_element_array).to receive(:first).with(no_args).and_return(1)
  allow(three_element_array).to receive(:first).with(1).and_return([1])
  ```

## Traits
  ```ruby
  trait :with_associations do
    property { build_stubbed(:property) }
  end

  create(:listing, :with_associations)
  ```
