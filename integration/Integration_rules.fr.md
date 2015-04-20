# Règles d'intégration
Définition des règles de nommage utilisé sur les projet. L'objectif de ce document est d'uniformiser les règles au travers des projets en s'appuyant sur l'expérience acquise avec les précédents.  
L'objectif étant d'accroître la maintenabilité des projets tout en optimisant leur conception du point de vue de l'intégration.

<br>

### Péambule

Ce que l'on appellera **page** ici fait référence aux templates encadrant une page au sens de l'utilisateur (e.g. Home, fiche produit, etc.).  
Ce que l'on appellera **fragment** ici fait références aux éléments visuel se répétant au travers du site sans pour autant n'appartenir qu'à une seule **page** (e.g. une sidebar, un miniature d'article, une liste, etc.).

<br>

### Index

 1. [HTML](#html)
  - [Pages](#pages)
  - [Fragments](#fragments)
  - [Elements enfants](#elements-enfants)
 2. [LESS](#less)
  - [Arborescence](#arborescence)
  - [Construction des fichiers](#construction-des-fichiers)

<br>

### HTML

#### Pages


Chaques **page** est défini par un `id` unique qui servira de base pour toute les éventuelles déclinaisons. Cet identifiant est complété par la `class` de déclaration d'une page : `.page`.
<br>
```html
<section id="product" class="page">
    <!-- <p>Content</p> -->
</section>
```
<br>
L'utilisation d'un `id` unique permettra la déclinaison d'un template à chaque fois que cela sera nécessaire et cela sans altérer le template initial. Pour décliner un template de **page** il convient cependant d'utiliser une `class` pour l'identifier car la définition de plusieurs `id` [n'est pas recommandé](http://www.w3.org/TR/xhtml1/#h-4.10).  
Pour des raison de compréhension, la `class` indiquant la déclinaison d'un template de page sera préfixé par l'`id` de la page et séparé par un `-`.
<br>
```html
<section id="product" class="page product-sponsored">
    <!-- <p>Sponsored content</p> -->
</section>
```
<br>
Il est également possible de modifier un ensemble de **page** par la déclinaison de la `class` `.page`. Selon ka même logique que la déclinaison des templates, la déclinaision des pages s'établis grâce à l'ajout d'une `class` préfixé par le nom de l'élément décliné, ici une `.page`.

```html
<section id="product" class="page page-archive product-sponsored">
    <!-- <p>Archived sponsored content</p> -->
</section>
```
<br>
En suivant cette logique, il est possible de délciner chaques pages en plusieurs mais également de faire déclinaisons en cascade.
<br>
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

<br>

#### Fragments

Au même titre que les pages, les **fragment** doivent être identifié clairement. Cependant, il est très probable que ces fragments apparaîssent plusieurs fois dans le DOM aussi l'identification de ces éléments devra se faire par un `class`.
<br><br>
> Malgré ce constat, il est vrai ue certain élément correspondant à la description d'un **fragment** ne se répèteront jamais plusieurs fois dans une page (e.g. une sidebar ou un header). Dans ces cas là, il est laissé au jugement du développeur le choix d'utiliser un `id`.

<br>
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

<br>

> Il est également possible d'utiliser les crochets dans l'attribut `class` pour améliorer la lisibilité    
```html
<article class="project [ project-archive project-archive-design project-archive-design-external ] ">
    <!-- <p>Project content</p> -->
</article>
```  
> Il est pertinent dans ces cas là de séparer le nom du **fragment** de ses déclinaisons.

<br>

#### Elements enfants

Les **pages** et les **fragments** sont donc définis comme des éléments conteneurs. Pour créer des templates riches ou tout simplement de taille plus importante, il faut donc des éléments enfants appartenant spécifiquement à un conteneur (quelque soit sont type).

<br>

```html
<section id="home" class="page [ page-project ]">

	<article class="project [ project-archive ] ">
	
		<h2>Project title</h2>
		
		<time>21 dec 2015</time>
		
		<p>Project content</p>
		
	</article>
	
</section>
```

<br>

L'utilisation sémantique des tag HTML n'étant pas suffisante dans la plupart des cas, il faut qualifier ces éléments. Pour des raisons d'homogénéité, tous les éléments seront qualifié et non pas seulement balise qui en ont la nécessité. Les conventions de nommage des éléments enfants sont également très proche de celle des conteneurs pour 2 raisons. Tout d'abord il est très important d'avoir une homogénéité à travers tout les éléments du site mais aussi pour montrer clairement l'appartenance des enfants à tel ou tel conteneur.

Chaque enfants va donc recevoir une `class` définissant clairement sa nature à laquelle on va préfixer le nom du conteneur parent. Les deux parties étant séparé par `--`. Ainsi, le titre d'une page se verra nommer `.page--title` et la date d'un article sera `.article--date`.

<br>

> A noter que le nom de l'élément peut être composé de plusieurs mots pour le qualifier clairement . Dans ce cas là, on utilisera le camel case pour l'identifier (e.g. `.article--publicationDate`)

<br>



```html
<section id="home" class="page [ page-project ]">
	
	<article class="project [ project-archive ] ">
	
		<h2 class="project--title">Project title</h2>
	
		<time class="project--publicationDate">21 dec 2015</time>
	
		<p class="project--content">Project content</p>
	
	</article>
	
</section>
```

<br>

Toutes ces règles sont bien sûr combinable entres-elles. Dans le cas d'un éléments enfants appartenant uniquement à une déclinaison donnée d'un conteneur, c'est le nom de cette déclinaison qui servira de préfix à l'élément.

<br>

```html
<section id="home" class="page [ page-project ]">

	<article class="project [ project-archive ] ">
	
		<h2 class="project--title">Project title</h2>
		
		<h3 class="project-archive--subtitle">Project sub title</h2>
		
		<time class="project--publicationDate">21 dec 2015</time>
		
		<p class="project--content">Project content</p>
		
	</article>
	
</section>
```
<br>
<br>
> De nombreux cas ne sont pas couvert par les règles édicté ici mais les principe fondamentaux étant clairement établit, il est laissé au jugement du développeur l'utilisation cohérente de ces lignes directrices.

<br>

### LESS

#### Arborescence

L'arborescence utilisé est défini selon l'organisation de ce [repository](https://github.com/Stuff90/LessTree.git).

```
less
│ └   style.less    
│
├───conf
│  │   colorscheme.less
│  │   font.less
│  │   grid.less
│  │   interface.less
│  │   layout.less
│  └   reset.less
│
├───fragments
│  │  sample.fragment.less
│  └  xxx.fragment.less
│
├───pages
│  │  sample.page.less
│  └  xxx.page.less
│
└───libraries
    └  xxx
```
On retrouve ici la même séparation entre les **pages** et les **fragments**. Les deux types de conteneurs ont le pattern de fichier `name.type.less` (une **page** sera nommé `home.page.less` et un **fragment** `list.fragment.less`). De cette façon, aucun doute ne pourra être soulevé quant à la nature de l'éléments contenu dans le fichier.

<br>

#### Construction des fichiers

##### Conteneurs et éléments enfants

A l'exception des fichiers de configuration, toutes les feuilles de style suivent le même schema. Le conteneur va êtres défini en premier et contiendra toute ses définition filles de sorte qu'une fois compilé, le nom du conteneur tienne lieu de `namespace`.


Fichier `product.page.less` :
```less
#product {
	background-color: teal;
	color: tomato;

	.product--title {
		font-weight: 500;
	}
	.product--availability {
		font-size: 1.2rem;
	}
}
```

Fichier `author.fragment.less` :
```less
.author {
	width: 5rem;
	height: 5rem;

	.author--firstName, .author--lastName {
		font-size: .8rem;
	}
	.author--lastName {
		color: tan;
	}
}
```
<br>
> Bien que l'exemple n'en fasse pas mention, il est possible d'utiliser l'opérateur `>`  pour qualifier les sélecteurs plus précisément.

<br>

##### Déclinaisons

Pour la définition 

##### Media queries


















