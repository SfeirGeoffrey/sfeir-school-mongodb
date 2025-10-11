<!-- .slide: class="with-code inconsolata"-->
# Explication d'une requête
- MongoDB nous offre la possibilité d'expliquer comment il traite une requête
```bash
db.collections.find().explain()
```
<!-- .element: class="big-code"-->
<br/><br/>

- Il existe une granularité dans les détails de l'explication
    - queryPlanner
    - executionStats
    - allPlansExecution
Notes: 
- queryPlanner => il s'agit du plan gagnant
- executionStats => il s'agit d'information précise sur le temps d'éxécution de la requête, du nombre de documents examinés, de quels indexes choisis
- allPlansExecution => il s'agit ici de montrer tous les plans qui ont été exécutés, même les moins performants

 ##==##

 <!-- .slide-->
 # Un exemple en image
 ![h-800 full-center](assets/images/school/indexation-performance/explain-query-plan.png)

