# Exercise 002 - Targeting

This exercise is about [SHACL targets](https://www.w3.org/TR/shacl/#targets)

Below you'll find some data about superheroes.
The aim of this exercise is to learn about targeting specific pieces of data using SHACL shapes.

We're going to be using the excellent [SHACL Playground](https://shacl.org/playground/) for these exercises.

This exercise has multiple parts:
* [Part a](#part-a)
* [Part b](#part-b)
* [Part c](#part-c)

Ok, lets get to it.

## Part a

Given the following data file

__Data__:
```
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix schema: <http://schema.org/> .
@prefix hero: <http://data.superheros.com/def/superhero#> .
@prefix : <http://data.superheros.com/id/superhero/> .

:Superman 
  rdfs:label "Superman" ;
  schema:gender schema:Female  ;
.

:WonderWoman a hero:Superhero ;
  rdfs:label "Wonder woman" ;
.

:Catwoman a hero:Superhero ;
.
```

Let's see if we can add statements to the following shape to target Superman specifically in our data.

__Shapes__:
```
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix schema: <http://schema.org/> .
@prefix sh: <http://www.w3.org/ns/shacl#> .
@prefix hero: <http://data.superheros.com/def/superhero#> .
@prefix ss: <http://data.superheros.com/id/shape/> .
@prefix : <http://data.superheros.com/id/superhero/> .

ss:SupermanShape a sh:NodeShape ;
  #-- insert here --#
  sh:property [
    sh:path schema:gender ;
    sh:hasValue schema:Male ;
    sh:minCount 1 ;
    sh:maxCount 1 ;
    sh:message "Should have one gender: Male" ;
  ] ;
.
```

The goal is to get the following result from executing the shape validation

__Validation result__:
```
[
	a sh:ValidationResult ;
	sh:resultSeverity sh:Violation ;
	sh:sourceConstraintComponent sh:HasValueConstraintComponent ;
	sh:sourceShape _:n1237 ; # blank node id varies every time
	sh:focusNode <http://data.superheros.com/id/superhero/Superman> ;
	sh:resultPath schema:gender ;
	sh:resultMessage "Should have one gender: Male" ;
] .
```

Did you manage? Great!

## Part b
In exercise [002-a](#002-a) we've learned how to target a specific node. However, it is often useful to target nodes of a certain type using the same shape. Luckily we can do this with SHACL as well.

Using the same data file and shapes file as above, alter the data file and the shapes file to target all superheroes in the data file. You might have to add some statements to the data as well...

The aim is to get the following result

__Validation result__:
```
[
	a sh:ValidationResult ;
	sh:resultSeverity sh:Violation ;
	sh:sourceConstraintComponent sh:HasValueConstraintComponent ;
	sh:sourceShape _:n125 ;
	sh:focusNode <http://data.superheros.com/id/superhero/Superman> ;
	sh:resultPath schema:gender ;
	sh:resultMessage "Should have one gender: Male" ;
] .
[
	a sh:ValidationResult ;
	sh:resultSeverity sh:Violation ;
	sh:sourceConstraintComponent sh:HasValueConstraintComponent ;
	sh:sourceShape _:n125 ;
	sh:focusNode <http://data.superheros.com/id/superhero/WonderWoman> ;
	sh:resultPath schema:gender ;
	sh:resultMessage "Should have one gender: Male" ;
] .
[
	a sh:ValidationResult ;
	sh:resultSeverity sh:Violation ;
	sh:sourceConstraintComponent sh:MinCountConstraintComponent ;
	sh:sourceShape _:n125 ;
	sh:focusNode <http://data.superheros.com/id/superhero/WonderWoman> ;
	sh:resultPath schema:gender ;
	sh:resultMessage "Should have one gender: Male" ;
] .
[
	a sh:ValidationResult ;
	sh:resultSeverity sh:Violation ;
	sh:sourceConstraintComponent sh:HasValueConstraintComponent ;
	sh:sourceShape _:n125 ;
	sh:focusNode <http://data.superheros.com/id/superhero/Catwoman> ;
	sh:resultPath schema:gender ;
	sh:resultMessage "Should have one gender: Male" ;
] .
[
	a sh:ValidationResult ;
	sh:resultSeverity sh:Violation ;
	sh:sourceConstraintComponent sh:MinCountConstraintComponent ;
	sh:sourceShape _:n125 ;
	sh:focusNode <http://data.superheros.com/id/superhero/Catwoman> ;
	sh:resultPath schema:gender ;
	sh:resultMessage "Should have one gender: Male" ;
] .
```

__Bonus question__: Why are there 2 violations for `:WonderWoman` and `:Catwoman`?

## Part c
We've seen how we can target specific nodes directly, as well as how to target classes of nodes. You're almost ready for the big leagues..

But SHACL can do more than that. Another useful way to target nodes is by targeting a property of the node (or nodes).

Let's use the same data and shapes again, only now we want our shape to only validate those superheroes that have an `rdfs:label`.

This should be the result

__Validation result__:
```
[
	a sh:ValidationResult ;
	sh:resultSeverity sh:Violation ;
	sh:sourceConstraintComponent sh:HasValueConstraintComponent ;
	sh:sourceShape _:n680 ;
	sh:focusNode <http://data.superheros.com/id/superhero/Superman> ;
	sh:resultPath schema:gender ;
	sh:resultMessage "Should have one gender: Male" ;
] .
[
	a sh:ValidationResult ;
	sh:resultSeverity sh:Violation ;
	sh:sourceConstraintComponent sh:HasValueConstraintComponent ;
	sh:sourceShape _:n680 ;
	sh:focusNode <http://data.superheros.com/id/superhero/WonderWoman> ;
	sh:resultPath schema:gender ;
	sh:resultMessage "Should have one gender: Male" ;
] .
[
	a sh:ValidationResult ;
	sh:resultSeverity sh:Violation ;
	sh:sourceConstraintComponent sh:MinCountConstraintComponent ;
	sh:sourceShape _:n680 ;
	sh:focusNode <http://data.superheros.com/id/superhero/WonderWoman> ;
	sh:resultPath schema:gender ;
	sh:resultMessage "Should have one gender: Male" ;
] .
```

Woohoo! You now know how to target data for validation using SHACL shapes.

## Next
[--> Exercise 003](exercise003)
