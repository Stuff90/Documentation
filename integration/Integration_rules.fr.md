# Règles d'intégration
Définition des règles de nommage utilisé sur les projet. L'objectif de ce document est d'uniformiser les règles au travers des projets en s'appuyant sur l'expérience acquise avec les précédents.  
L'objectif étant d'accroître la maintenabilité des projets tout en optimisant leur conception du point de vue de l'intégration.

### Péambule

Ce que l'on appellera **page** ici fait référence aux templates encadrant une page au sens de l'utilisateur (e.g. Home, fiche produit, etc.).  
Ce que l'on appellera **fragment** ici fait références aux éléments visuel se répétant au travers du site sans pour autant n'appartenir qu'à une seule **page** (e.g. une sidebar, un miniature d'article, une liste, etc.).

### HTML

##### Pages


Chaques **page** est défini par un `id` unique qui servira de base pour toute les éventuelles déclinaisons. Cet identifiant est complété par la `class` de déclaration d'une page : `.page`.

```html
<section id="product" class="page">
    <!-- <p>Content</p> -->
</section>
```

L'utilisation d'un `id` unique permettra la déclinaison d'un template à chaque fois que cela sera nécessaire et cela sans altérer le template initial. Pour décliner un template de **page** il convient cependant d'utiliser une `class` pour l'identifier car la définition de plusieurs `id` [n'est pas recommandé](http://www.w3.org/TR/xhtml1/#h-4.10).  
Pour des raison de compréhension, la `class` indiquant la déclinaison d'un template de page sera préfixé par l'`id` de la page et séparé par un `-`.

```html
<section id="product" class="page product-sponsored">
    <!-- <p>Sponsored content</p> -->
</section>
```

Il est également possible de modifier un ensemble de **page** par la déclinaison de la `class` `.page`. Selon ka même logique que la déclinaison des templates, la déclinaision des pages s'établis grâce à l'ajout d'une `class` préfixé par le nom de l'élément décliné, ici une `.page`.

```html
<section id="product" class="page page-archive product-sponsored">
    <!-- <p>Archived sponsored content</p> -->
</section>
```

En suivant cette logique, il est possible de délciner chaques pages en plusieurs mais également de faire déclinaisons en cascade.

```html
<section id="product" class="page page-archive page-archive-2015 page-archive-2015-article  product-sponsored product-sponsored-dior product-sponsored-dior-shoe">
    <!-- <p>Content</p> -->
</section>
```
<br>
> Si de nombreuses déclinaisons s'enchaînent comme on peut le voir dans l'exemple ci-dessus, il est possible de grouper les classes les définissants en utilisant des `[]`.  
> L'utilisation des crochets dans l'attribut `class` est sans conséquences pour l'intertprétation du HTML puisque ces caractère ne sont pas reconnu en tant qu'attributs valides et sont donc ignoré par l'interpréteur. Idem en CSS, n'étant pas des selecteurs valides, la définition de style sur un crochet ne fonctionnera pas et n'impactera pas non plus les selecteurs tels que `.my-input[type=text]`.

```html
<section id="product" class="[ page page-archive page-archive-2015 page-archive-2015-article ] [ product-sponsored product-sponsored-dior product-sponsored-dior-shoe ]">
    <!-- <p>Content</p> -->
</section>
```  
Pour en savoir un peu plus sur cette pratique, un article intéressant sur le sujet est disponible [sur CSS Wizardy](http://csswizardry.com/2014/05/grouping-related-classes-in-your-markup/).

##### Fragments

Au même titre que les pages, les **fragment** doivent être identifié clairement. Cependant, il est très probable que ces fragments apparaîssent plusieurs fois dans le DOM aussi l'identification de ces éléments devra se faire par un `class`.

> Malgré ce constat, il est vrai ue certain élément correspondant à la description d'un **fragment** ne se répèteront jamais plusieurs fois dans une page (e.g. une sidebar ou un header). Dans ces cas là, il est laissé au jugement du développeur le choix d'utiliser un `id`.

Pour que leur utilisation soit pertinente, il convient de nommer les **fragments** de la manière la plus explicite possible.


```html
<article class="project">
    <!-- <p>Project content</p> -->
</article>
```  

Les déclinaisons des **fragments** fonctionnent de la même manière que les **pages**.


```html
<article class="project project-archive project-archive-design project-archive-design-external">
    <!-- <p>Project content</p> -->
</article>
```

> Il est également possible d'utiliser les crochets dans l'attribut `class` pour améliorer la lisibilité  
```html
<article class="project [ project-archive project-archive-design project-archive-design-external ] ">
    <!-- <p>Project content</p> -->
</article>
```  
Il est pertinent dans ces cas là de séparer le nom du **fragment** de ses déclinaisons.

### LESS

##### Arborescence
##### Construction des fichiers





















