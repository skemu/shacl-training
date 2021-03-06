# 001 - Superhero ontology

In this exercise we're going to extend an OWL ontology describing the universe of superheroes! The universe is partially described, but it's up to you to complete it. 

The venn diagram describing the complete universe is depicted below.

![Superheroes venn diagram](superheroes-venn.png)

Some notes:

* A hero can't be a villain and a villain can't be a hero.
* A list of superpowers. Let's assume that the only superpowers in this universe are:
  * AcceleratedHealing
  * EnhancedHearing
  * EnhancedSight
  * FireResistance
  * Flight
  * HeatResistance
  * Longevity
  * SuperSpeed
  * SuperStrength
  * Vision-Heat
  * Vision-X-Ray
* Take a good look at the `rdfs:comment` properties for indications!

```@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix owl: <http://www.w3.org/2002/07/owl#> .
@prefix schema: <http://schema.org/> .
@prefix hero: <http://data.superheros.com/def/superhero#> .

hero:Being a owl:Class ;
  rdfs:comment "A real or imaginary living creature or entity" ;
.

hero:Human a owl:Class ;
  rdfs:comment "A human being" ;
  rdfs:subClassOf hero:Being ;
.

hero:Hero a owl:Class ;
  rdfs:comment "A being that does heroic stuff" ;
  rdfs:subClassOf hero:Being ;
.

hero:Villain a owl:Class ;
  rdfs:comment "A being that does villainous stuff" ;
  rdfs:subClassOf hero:Being ;
  # - insert here - #
.

hero:SuperBeing a owl:Class ;
  rdfs:comment "A being with at least one superpower." ;
  owl:equivalentClass [
    a owl:Restriction ;
    #- insert here -#
  ] ;
.

hero:SuperHuman a owl:Class ;
  rdfs:comment "A human super-being" ;
  owl:equivalentClass [
    owl:intersectionOf (
      hero:Human
      #- insert here -#
    ) ;
  ] ;
.

hero:Superhero a owl:Class ;
  rdfs:comment "A super-being that is also a hero" ;
  #- insert here -#
.

hero:Ability a owl:Class ;
  rdfs:comment "Something a being can do" ;
.

hero:Superpower a owl:Class ;
  rdfs:comment "A supernatural ability" ;
  # - insert here - #
.

hero:hasAbility a owl:ObjectProperty ;
  rdfs:domain hero:Being ;
  rdfs:range hero:Ability ;
.

hero:hasSuperpower a owl:ObjectProperty ;
  rdfs:range hero:Superpower ;
.
```
