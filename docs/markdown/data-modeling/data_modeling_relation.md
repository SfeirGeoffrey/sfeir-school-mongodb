<!-- .slide-->
# Les différents types de relations
- Il existe <b>trois</b> types de relations classiques entres les données:
    - One to one
    - one to many
    - many to many

##==##

<!-- .slide-->
# La relation One to One 
- <b>Exemple:</b> Un patient et son historique médical
<br/><br/>

 ##==##

 <!-- .slide: class="with-code inconsolata"-->
 # Exemple - contexte
 Un patron et l'adresse de son restaurant: On suppose que le patron n'a qu'un seul restaurant
 <br/><br/>

```json
{
   _id: "joe",
   name: "Joe Bookreader"
}

{
   patron_id: "joe",
   street: "123 Fake Street",
   city: "Faketon",
   state: "MA",
   zip: "12345"
}
```
<!-- .element: class="medium-code"-->

##==##

<!-- .slide: class="with-code inconsolata"-->
# Exemple - solution
```json
{
   _id: "joe",
   name: "Joe Bookreader",
   address: {
              street: "123 Fake Street",
              city: "Faketon",
              state: "MA",
              zip: "12345"
            }
}
```
<!-- .element: class="medium-code"-->
<br/>

##==##

<!-- .slide -->
# La relation One to Many
- <b>Exemple:</b> Une ville et ses habitants
<br/><br/>

- 1 seule façon de modéliser ce type de relation:
    - Normalization en utilisant le true linking <br/><br/>
    <!-- .element: class="important" -->
	
- Le true linking consiste à réaliser une référence par _id qui est unique et surtout qui n'est pas censée être modifiée => on supprime ici l'inconsistence
<br/><br/>
- Et si l'on était dans une relation ou le Many se trouve être un few?
<!-- .element: class="bold" -->


##==##

<!-- .slide: class="with-code inconsolata"-->
# Exemple - contexte

- Un patron et l'adresse de son restaurant: On suppose que le patron a plusieurs restaurants
<br/><br/>

```json
{
   _id: "joe",
   name: "Joe Bookreader"
}

{
   patron_id: "joe",
   street: "123 Fake Street",
   city: "Faketon",
   state: "MA",
   zip: "12345"
}

{
   patron_id: "joe",
   street: "1 Some Other Street",
   city: "Boston",
   state: "MA",
   zip: "12345"
}
```
<!-- .element: class="medium-code" -->

##==##

<!-- .slide: class="with-code inconsolata"-->
# Exemple - solution
```json
{
   _id: "joe",
   name: "Joe Bookreader",
   addresses: [
                {
                  street: "123 Fake Street",
                  city: "Faketon",
                  state: "MA",
                  zip: "12345"
                },
                {
                  street: "1 Some Other Street",
                  city: "Boston",
                  state: "MA",
                  zip: "12345"
                }
              ]
 }
 ```
 <!-- .element: class="medium-code" -->

 ##==##

 <!-- .slide: class="with-code inconsolata"-->
 # Exemple - contexte
- Une maison de publication de livres
<br/><br/>

```json
{
  name: "O'Reilly Media",
  founded: 1980,
  location: "CA",
}
{
  title: "MongoDB: The Definitive Guide",
  author: [ "Kristina Chodorow", "Mike Dirolf" ],
  published_date: ISODate("2010-09-24"),
  pages: 216,
  language: "English",
}
{
  title: "50 Tips and Tricks for MongoDB Developer",
  author: "Kristina Chodorow",
  published_date: ISODate("2011-05-06"),
  pages: 68,
  language: "English",
}
```
<!-- .element: class="medium-code" -->
<br/>

##==##

<!-- .slide: class="with-code inconsolata"-->
# Exemple - solution
```json
{
   _id: "oreilly",
   name: "O'Reilly Media",
   founded: 1980,
   location: "CA"
}

{
   _id: 123456789,
   title: "MongoDB: The Definitive Guide",
   author: [ "Kristina Chodorow", "Mike Dirolf" ],
   published_date: ISODate("2010-09-24"),
   pages: 216,
   language: "English",

   publisher_id: "oreilly"

}

{
   _id: 234567890,
   title: "50 Tips and Tricks for MongoDB Developer",
   author: "Kristina Chodorow",
   published_date: ISODate("2011-05-06"),
   pages: 68,
   language: "English",

   publisher_id: "oreilly"

}
```
<!-- .element: class="medium-code" -->


##==##

<!-- .slide: class="sfeir-basic-slide"-->
# La relation Many to Many
- <b>Exemple: </b> Professeurs et élèves: un professeur a plusieurs élèves et réciproquement <br/><br/>
- 1 façon de modéliser ce type de relation:
    - Normalization en utilisant le two way true linking <br/><br/>
    <!-- .element: class="important" -->
- Two way true linking consiste tout simplement à réaliser un tableau dans chaque document contenant les id relationnels

##==##

<!-- .slide: class="with-code inconsolata"-->
# Exemple - contexte
```json
{
  id: '1',
  name: 'Nicolas',
  job: 'student'
}
{
  id: '2',
  name: 'Renaud',
  job: 'student'
}
{
  id: '11',
  name: 'Groche',
  job: 'Teacher'
}
{
  id: '12',
  name: 'Volpy',
  job: 'Teacher'
}
```
<!-- .element: class="medium-code" -->

##==##

<!-- .slide: class="with-code inconsolata"-->
# Exemple - solution
```json
{
  id: '1',
  name: 'Nicolas',
  job: 'student'
  teachers: [11, 12]
}
{
  id: '2',
  name: 'Renaud',
  job: 'student'
  teachers: [11, 12]
}
{
  id: '11',
  name: 'Groche',
  job: 'Teacher'
  students: [1,2]
}
{
  id: '12',
  name: 'Volpy',
  job: 'Teacher'
  students: [1,2]
}
```
<!-- .element: class="medium-code" -->
