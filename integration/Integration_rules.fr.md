# Règles d'intégration
Définition des règles de nommage utilisé sur les projets. L'objectif de ce document est d'uniformiser les règles au travers des projets en s'appuyant sur l'expérience acquise avec les précédents.  
L'objectif étant d'accroître la maintenabilité des projets tout en optimisant leur conception du point de vue de l'intégration.

<br>

### Préambule

Ce que l'on appellera **page** ici fait référence aux templates encadrant une page au sens de l'utilisateur (e.g. Home, fiche produit, etc.).  
Ce que l'on appellera **fragment** ici fait référence aux éléments visuels se répétant au travers du site sans pour autant n'appartenir qu'à une seule **page** (e.g. une sidebar, un miniature d'article, une liste, etc.).

<br>

### Index

 1. [HTML](#html)
  - [Pages](#pages)
  - [Fragments](#fragments)
  - [Éléments enfants](#%C3%89l%C3%A9ments-enfants)
 2. [LESS](#less)
  - [Arborescence](#arborescence)
  - [Construction des fichiers](#construction-des-fichiers)

<br>

### HTML

#### Pages


Chaque **page** est définie par un `id` unique qui servira de base pour toutes les éventuelles déclinaisons. Cet identifiant est complété par la `class` de déclaration d'une page : `.page`.
<br>
```html
<section id="product" class="page">
    <!-- <p>Content</p> -->
</section>
```
<br>
L'utilisation d'un `id` unique permettra la déclinaison d'un template à chaque fois que cela sera nécessaire et cela sans altérer le template initial. Pour décliner un template de **page** il convient cependant d'utiliser une `class` pour l'identifier car la définition de plusieurs `id` [n'est pas recommandée](http://www.w3.org/TR/xhtml1/#h-4.10).  
Pour des raisons de compréhension, la `class` indiquant la déclinaison d'un template de page sera préfixée par l'`id` de la page et séparée par un `-`.
<br>
```html
<section id="product" class="page product-sponsored">
    <!-- <p>Sponsored content</p> -->
</section>
```
<br>
Il est également possible de modifier un ensemble de **pages** par la déclinaison de la `class` `.page`. Selon la même logique que la déclinaison des templates, la déclinaison des pages s'établit grâce à l'ajout d'une `class` préfixée par le nom de l'élément décliné, ici une `.page`.

```html
<section id="product" class="page page-archive product-sponsored">
    <!-- <p>Archived sponsored content</p> -->
</section>
```
<br>
En suivant cette logique, il est possible de décliner chaque page en plusieurs déclinaisons mais également de faire des déclinaisons en cascade.
<br>
```html
<section id="product" class="page page-archive page-archive-2015 page-archive-2015-article  product-sponsored product-sponsored-dior product-sponsored-dior-shoe">
    <!-- <p>Content</p> -->
</section>
```
<br>
> Si de nombreuses déclinaisons s'enchaînent comme on peut le voir dans l'exemple ci-dessus, il est possible de grouper les classes les définissant en utilisant des `[]`.  
> L'utilisation des crochets dans l'attribut `class` est sans conséquences pour l'interprétation du HTML puisque ces caractères ne sont pas reconnus en tant qu'attributs valides et sont donc ignorés par l'interpréteur. Idem en CSS, n'étant pas des sélecteurs valides, la définition de style sur un crochet ne fonctionnera pas et n'impactera pas non plus les sélecteurs tels que `.my-input[type=text]`.  
```html
<section id="product" class="page [ page-archive page-archive-2015 page-archive-2015-article ] [ product-sponsored product-sponsored-dior product-sponsored-dior-shoe ]">
    <!-- <p>Content</p> -->
</section>
```  
Pour en savoir un peu plus sur cette pratique, un article intéressant sur le sujet est disponible [sur CSS Wizardy](http://csswizardry.com/2014/05/grouping-related-classes-in-your-markup/).

<br>

#### Fragments

Au même titre que les pages, les **fragments** doivent être identifiés clairement. Cependant, il est très probable que ces fragments apparaissent plusieurs fois dans le DOM aussi l'identification de ces éléments devra se faire par une `class`.
<br><br>
> Malgré ce constat, il est vrai que certains éléments correspondant à la description d'un **fragment** ne se répèteront jamais plusieurs fois dans une page (e.g. une sidebar ou un header). Dans ces cas-là, il est laissé au jugement du développeur le choix d'utiliser un `id`.

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
> Il est pertinent dans ces cas-là de séparer le nom du **fragment** de ses déclinaisons.

<br>

#### Éléments enfants

Les **pages** et les **fragments** sont donc définis comme des éléments conteneurs. Pour créer des templates riches ou tout simplement de taille plus importante, il faut donc des éléments enfants appartenant spécifiquement à un conteneur (quelque soit son type).

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

L'utilisation sémantique des tags HTML n'étant pas suffisante dans la plupart des cas, il faut qualifier ces éléments. Pour des raisons d'homogénéité, tous les éléments seront qualifiés et non pas seulement les balises qui en ont la nécessité. Les conventions de nommage des éléments enfants sont également très proche de celle des conteneurs pour 2 raisons. Tout d'abord il est très important d'avoir une homogénéité à travers tous les éléments du site mais aussi pour montrer clairement l'appartenance des enfants à tel ou tel conteneur.

Chaque enfant va donc recevoir une `class` définissant clairement sa nature à laquelle on va préfixer le nom du conteneur parent. Les deux parties étant séparées par `--`. Ainsi, le titre d'une page se verra nommer `.page--title` et la date d'un article sera `.article--date`.

<br>

> A noter que le nom de l'élément peut être composé de plusieurs mots pour le qualifier clairement . Dans ce cas-là, on utilisera le camel case pour l'identifier (e.g. `.article--publicationDate`)

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

Toutes ces règles sont bien sûr combinables entres-elles. Dans le cas d'un élément enfant appartenant uniquement à une déclinaison donnée d'un conteneur, c'est le nom de cette déclinaison qui servira de préfixe à l'élément.

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
> De nombreux cas ne sont pas couverts par les règles édictées ici mais les principes fondamentaux étant clairement établis, il est laissé au jugement du développeur l'utilisation cohérente de ces lignes directrices.

<br>

### LESS

#### Arborescence

L'arborescence utilisée est définie selon l'organisation de ce [repository](https://github.com/Stuff90/LessTree.git).

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
On retrouve ici la même séparation entre les **pages** et les **fragments**. Les deux types de conteneurs ont le pattern de fichier `name.type.less` (une **page** sera nommée `home.page.less` et un **fragment** `list.fragment.less`). De cette façon, aucun doute ne pourra être soulevé quant à la nature de l'élément contenu dans le fichier.

<br>

#### Construction des fichiers

La construction des fichiers LESS est complexe car la longueur de ceux-ci rend souvent la lisibilité difficile. Cela est d'autant plus vrai lorsque le projet comprend de nombreuses déclinaisons dans ses templates.

##### Conteneurs et éléments enfants

A l'exception des fichiers de configuration, toutes les feuilles de style suivent le même schéma. Le conteneur va être défini en premier et contiendra toute ses définitions filles de sorte qu'une fois compilé, le nom du conteneur tienne lieu de `namespace`.


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

La définition des déclinaisons d'un template se trouve dans le même fichier que l'élément décliné. Ainsi, dans le fichier `product.page.less` nous trouverons tous les templates de produits différents.  
Pour décliner un template, on utilise la fonction `:extend()` fournie par LESS.


Fichier `product.page.less` :
```less
.product-sale:extend(#product)
	margin: auto;

	.product--title {
		font-weight: 300;
	}
}
```

Fichier `author.fragment.less` :
```less
.author-premium:extend(.author) {
	border: solid .2rem @black;

	.author--lastName {
		color: chocolate;
	}
}
```
<br>

Dans le cas d'un déclinaison utilisant le style des enfants de la classe parente sur ses propre enfants, il convient d'utiliser le mot clef `all`.

```less
.author {
	border: solid .2rem @black;

	.author--lastName {
		color: chocolate;
	}
}

.author-premium:extend(.author all) {
	border: solid .2rem @black;

	.author--lastName {
		// "color: chocolate;" is applied but come from the parent
		font-style: italic;
	}
}
```

<br>

> Pour plus de renseignement au sujet de la fonction `:extend()` dans LESS, la [documentation](http://lesscss.org/features/#extend-feature) donne de nombreuses informations et exemples.

<br>

##### Media queries


Les changements de style en fonction de la taille du viewport peuvent être gérés de deux façons. Si le projet est d'envergure et/ou qu'il comprend de nombreux breakpoints, il sera plus avantageux de disposer d'un fichier par breakpoint traité. Dans le cas d'un projet plus réduit ou bien que le style contenu dans des media queries est relativement réduit, il sera plus avantageux de le laisser dans le même fichier.

<br>

Dans le cas de l'utilisation de plusieurs fichier, la convention de nommage de ceux-ci doit être cohérente par rapport aux autres fichier LESS. Il convient donc d'utiliser la syntaxe `name.device.type.less` (une page sera donc nommé `product.mobile.page.less`).  
L'arborescence quant à elle reste la même puisque le fichier dédié à la media query se placera dans le même répertoire que le parent.


```
less
├───pages
│  │  sample.page.less
│  │  sample.mobile.page.less
│  └  xxx.page.less
│
[...]
```

Au début de ce fichier dédié, il faut bien sûr rappeler le nom de l'élément surchargé. Il est également conseillé d'ajouter en commentaire la nature (et si besoin le role) et cette media query.
```less
// Mobile
// Devices with width <= 720

@media only screen and (max-width: 721px)
	#product {		
		.product--availability {
			font-size: 2rem;
		}
	}
}
```

<br>

Dans le cas de l'utilisation du même fichier, le role de la media query doit être clairement indiqué en commentaire avant sa définition. L'élément conteneur devra également être rappelé avant tout autre sélecteur pour que la gestion des priorités de l'interpréteur soit correctement appliquée.

```less
#product {
	background-color: teal;
	color: tomato;
	
	.product--availability {
		font-size: 1.2rem;
	}
}

// Mobile

@media only screen and (max-width: 720px)
	#product {		
		.product--availability {
			font-size: 2rem;
		}
	}
}
```

<br>

> La prise de décision pour l'utilisation d'un technique ou d'une autre peut être cornélienne car le périmètre du projet peut changer ou bien une V2 de celui-ci peut être demander etc. Pour se prémunir contre ces changements d'échelles il est tout à fait possible de changer l'organisation de ses fichiers en cours de projet.

<br>














