# Exercise 003 - Property paths

__Data__:
```
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix schema: <http://schema.org/> .
@prefix hero: <http://data.superheros.com/def/superhero#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix : <http://data.superheros.com/id/superhero/> .

:Superman
  rdfs:label "Superman" ;
  schema:gender schema:Male ;
  schema:birthPlace :Krypton ;
  schema:height [
    a schema:QuantitativeValue ;
    schema:value 191 ;
    schema:unit "cm" ;
  ] ;
  schema:weight [
    a schema:QuantitativeValue ;
    schema:value 101 ;
    schema:unit "kg" ;
  ] ;
  schema:subjectOf
    :supermanIMovie ,
    :supermanIIMovie ,
    :supermanIIIMovie ,
    :supermanIVMovie ,
    :supermanReturnsMovie ;
.

:supermanIMovie
  a schema:Movie ;
  schema:url <https://www.imdb.com/title/tt0078346/> ;
  schema:name "Superman" ;
  schema:description "Superman is a movie starring Christopher Reeve, Margot Kidder, and Gene Hackman. An alien orphan is sent from his dying planet to Earth, where he grows up to become his adoptive home's first and greatest superhero." ;
  schema:datePublished "1978-12-14"^^xsd:date ;
  schema:genre 
    "Action" ,
    "Adventure" ,
    "Drama" ,
    "Sci-Fi" ;
  schema:aggregateRating [
    a schema:AggregateRating ;
    schema:ratingCount 174547 ;
    schema:ratingValue 7.4 ;
  ] ;
  schema:actor [
    a schema:Person ;
    schema:url <https://www.imdb.com/name/nm0001659/> ;
    schema:name "Christopher Reeve" ;
  ] ;
.

:supermanIIMovie
  a schema:Movie ;
  schema:url <https://www.imdb.com/title/tt0081573/> ;
  schema:name "Superman II" ;
  schema:aggregateRating [
    a schema:AggregateRating ;
    schema:ratingCount 90568 ;
    schema:ratingValue 6 ;
  ] ;
  schema:actor [
    a schema:Person ;
    schema:url <https://www.imdb.com/name/nm0001659/> ;
    schema:name "Christopher Reeve" ;
  ] ;
.

:supermanIIIMovie
  a schema:Movie ;
  schema:url <https://www.imdb.com/title/tt0086393/> ;
  schema:name "Superman III" ;
  schema:aggregateRating [
    a schema:AggregateRating ;
    schema:ratingCount 59474 ;
    schema:ratingValue 4.9 ;
  ] ;
  schema:actor [
    a schema:Person ;
    schema:url <https://www.imdb.com/name/nm0001659/> ;
    schema:name "Christopher Reeve" ;
  ] ;
.

:superbadMovie
  a schema:Movie ;
  schema:url <https://www.imdb.com/title/tt0086393/> ;
  schema:name "Superbad" ;
  schema:aggregateRating [
    a schema:AggregateRating ;
    schema:ratingCount 481687 ;
    schema:ratingValue 7.6 ;
  ] ;
  schema:actor [
    a schema:Person ;
    schema:url <https://www.imdb.com/name/nm0148418/> ;
    schema:name "Michael Cera" ;
  ] , [
    a schema:Person ;
    schema:url <https://www.imdb.com/name/nm1706767/> ;
    schema:name "Jonah Hill" ;
  ] ;
.

:supermanIVMovie
  a schema:Movie ;
  schema:url <https://www.imdb.com/title/tt0094074/> ;
  schema:name "Superman IV" ;
  schema:aggregateRating [
    a schema:AggregateRating ;
    schema:ratingCount 39363 ;
    schema:ratingValue 3.7 ;
  ] ;
  schema:actor [
    a schema:Person ;
    schema:url <https://www.imdb.com/name/nm0001659/> ;
    schema:name "Christopher Reeve" ;
  ] ;
.

:supermanReturnsMovie
  a schema:Movie ;
  schema:url <https://www.imdb.com/title/tt0094074/> ;
  schema:name "Superman IV" ;
  schema:aggregateRating [
    a schema:AggregateRating ;
    schema:ratingCount 39363 ;
  ] ;
  schema:actor [
    a schema:Person ;
    schema:url <https://www.imdb.com/name/nm0746125/> ;
    schema:name "Brandon Routh" ;
  ] ;
.
```
## Part a

The dataset contains some superhero moviedata from IMDB! We want to use this data in our system to play around with movie ratings. To this end we want to make sure the ratings are using the correct datatype!
 
Extend the following shape to check that that __all__ movies have a rating and that all ratings are typed as `xsd:decimal`.

__Shapes__:
```
@prefix schema: <http://schema.org/> .
@prefix sh: <http://www.w3.org/ns/shacl#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix : <http://data.superheros.com/id/superhero/> .

:MovieList a sh:NodeShape ;
  #- insert here -#
.
```

Fix any data violations!

## Part b
We're organizing a Superman movie marathon. But we only want to watch movies with the original actor: Christopher Reeve. 

Make a shape that describes those movies!
Are there any movies that don't make the list?

__Shapes__:
```
@prefix schema: <http://schema.org/> .
@prefix sh: <http://www.w3.org/ns/shacl#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix : <http://data.superheros.com/id/superhero/> .

:ChristopherReeveMovieAboutSuperman a sh:NodeShape ;
  #- insert here -#
.
```

## Next
[--> Exercise 004](exercise004)
