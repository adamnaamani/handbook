# Design Patterns

## Table of Contents
1. [Memoization](#memoization)
1. [Lambda](#lambda)
1. [Currying](#currying)
1. [Atomic](#atomic)
1. [Domain Driven Design](#domain-driven-design)
1. [Null Object Pattern](#null-object-pattern)
1. [Yagni](#yagni)
1. [Unmarshalling](#unmarshalling)
1. [Fluent Interface](#fluent-interface)

## Memoization
An optimization technique used primarily to speed up computer programs by storing the results of expensive function calls and returning the cached result when the same inputs occur again.

Memoization is a technique you can use to speed up your accessor methods. It caches the results of methods that do time-consuming work, work that only needs to be done once. In Rails, you see memoization used so often that it even included a module that would memoize methods for you.

## Lambda
Lambda functions: anonymous, quick throwaway functions without naming them

## Currying
In mathematics and computer science, currying is the technique of translating the evaluation of a function that takes multiple arguments into evaluating a sequence of functions, each with a single argument.

## Atomic
Of or forming a single irreducible unit or component in a larger system.

## Domain Driven Design
Ubiquitous Language is the term Eric Evans uses in Domain Driven Design for the practice of building up a common, rigorous language between developers and users. This language should be based on the Domain Model used in the software - hence the need for it to be rigorous, since software doesn't cope well with ambiguity.

## Null Object Pattern
Provides an object as a surrogate for the lack of an object of a given type. The Null Object provides intelligent do nothing behavior, hiding the details from its collaborators.

Returns a new instance of `NullRelation`, which responds to every method that a normal instance of `Relation` would.
```ruby
class Buyer
  def property
    Property.none
  end
end
```

## YAGNI
"You aren't gonna need it" is a principle of extreme programming (XP) that states a programmer should not add functionality until deemed necessary.

## Unmarshalling
In computer science, unmarshalling or unmarshaling refers to the process of transforming a representation of an object that was used for storage or transmission to a representation of the object that is executable. A serialized object which was used for communication can not be processed by a computer program. An unmarshalling interface takes the serialized object and transforms it into an executable form.

## Fluent Interface
An object-oriented API designed for method chaining. It increases code legibility by creating a Domain-Specific Language (DSL).
```ruby
results.page(1).per_page(10)
```