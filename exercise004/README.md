# Exercise 004

Now, we want our dataset to only contain the elite superheroes that Superman knows. Superman's elite contact list if you will..
An elite superhero has at least __5__ superpowers!

__Data__ :
```
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix schema: <http://schema.org/> .
@prefix hero: <http://data.superheros.com/def/superhero#> .
@prefix : <http://data.superheros.com/id/superhero/> .

:Superman a hero:Superhero ;
  rdfs:label "Superman" ;
  schema:knows 
    :WonderWoman ,
    :Batman ,
    :Catwoman ;
.

:WonderWoman a hero:Superhero ;
  rdfs:label "Wonder woman" ;
  hero:hasSuperpower
    hero:AcceleratedHealing ,
    hero:EnhancedHearing ,
    hero:EnhancedSight ,
    hero:FireResistance ,
    hero:Flight ,
    hero:HeatResistance ,
    hero:Longevity ,
    hero:SuperSpeed ,
    hero:SuperStrength ,
    hero:Vision-Heat ,
    hero:Vision-X-Ray ;
.

:Batman a hero:Superhero ;
  rdfs:label "Batman" ;
  hero:hasSuperpower
    hero:HeatResistance ,
    hero:Longevity ,
    hero:Vision-Heat ;
.

:Catwoman a hero:Superhero ;
  rdfs:label "Catwoman" ;
  hero:hasSuperpower
    hero:AcceleratedHealing ,
    hero:EnhancedHearing ,
    hero:EnhancedSight ,
    hero:SuperSpeed ,
    hero:SuperStrength ;
.
```


Create a shapes graph to detect non-elite superhero contacts!
