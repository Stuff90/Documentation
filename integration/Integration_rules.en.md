# Integration rules

Defintion of naming rules to be used on projects. The aim of this document is to uniform rules through projects based on previous work experience.  
The final goal is to increase the maintainability of projects as well as optimizing integration.

<br>

### Preamble

The term **page** refer to templates containing an entire page from the final user point of view (e.g. Home, product, etc.).     
The term **fragment** refer to visual elements appearing multiple times throughout the website and also without belonging to only one **page**  (e.g. sidebar, article thumbnail, liste item, etc.).

<br>

### Index

 1. [HTML](#html)
  - [Pages](#pages)
  - [Fragments](#fragments)
  - [Childs elements](#childselements)
 2. [LESS](#less)
  - [File tree](#file-tree)
  - [Files structure](#files-structure)

<br>

### HTML

#### Pages

Each **page** is defined by an unique `id` which will be the root element for every potential declinations. This `id` is paired with the `class` dedicated to page declaration : `page`.

<br>

```html
<section id="product" class="page">
    <!-- <p>Content</p> -->
</section>
```
<br>

Using a unique `id` allow to decline a template anytime it would be necessary and this, without altering initial template. In order to decline a **page**, it is necessary to identify it with a `class`. Using several `id` on a element is [not recommended](http://www.w3.org/TR/xhtml1/#h-4.10).  
For understanding reasons, the `class` used to decline a template must be prefixed by the `id` of the page declined and splitted by a `-`.

<br>

```html
<section id="product" class="page product-sponsored">
    <!-- <p>Sponsored content</p> -->
</section>
```
<br>

It is also possible to edit several **pages** by declination of the `class`.

#### Fragments

#### Childs elements

### LESS

#### File tree

#### Files structure
