<!-- .slide: class="exercice"-->
# Exercice 14
## Lab
<br/>

Dans la collection students<br/><br/>
<!-- .element: class="bold" -->

- créer un index sur le champs de name<br/><br/>
- afficher tous les indexes disponibles sur cette collection<br/><br/>
 

##==##

<!-- .slide: class="exercice with-code inconsolata" -->
# Exercice 15
## Lab
<br/>

Soit l'index suivant:
<!-- .element: class="bold" -->


```json
{ first_name : 1, address.state: -1, address.city: -1, ssn: 1 }
```
<!-- .element: class="big-code" -->
<br/><br/>

Dans le dossier assets/exercice/sort-queries situé à la racine, fichier sort_queries, quelles queries utilisent l'index ci-dessus?

##==##

<!-- .slide: class="exercice with-code" -->
# Exercice 16
## Lab

Dans le dossier assets/exercice/explain, fichier explain se trouve une explication de query.
<!--.element: class="bold" -->
<br/>

- A l'aide de cette explication, quel index correspond à ce résultat :
    - { "address.state": 1, "name": 1, "stars": 1 }
    - { "address.state": 1, "stars": 1, "name": 1 }
    - { "address.state": 1, "name": 1 }
    - { "address.state": 1 }

##==##
<!-- .slide: class="transition-bg-sfeir-3 blue"-->
# Live Correction
