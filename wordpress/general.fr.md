# Wordpress

L'utilisation de Wordpress est souvent nécessaire pour de nombreux projets. Cependant, le moteur de blog n'est pas toujours pertinent dans sa version de base. De nombreux outils et règles d'utilisations ont donc été mis en place.

### Index

 1. [Installation](#installation)
  - [Wordpress](#wordpress)
  - [Dépendances](#dépendances)
 2. [Utilisation](#utilisation)
  - [Contenu](#contenu)
  - [Ressources](#ressources)
  - [Styles](#styles)
  - [Scripts](#scripts)
  - [Templates](#templates)
  - [Taxonomies](#taxonomies)
  - [Filtres](#filtres)

<br>

### Installation

#### Wordpress

La création d'un nouveau projet avec Wordpress peut être réalisé de nombreuses façons. Dans un souci d'homogénéité, nous utiliserons un outil de génération de projet appelé [Stonemason](https://github.com/Stuff90/stonemason). Cet outil est également maintenu par notre équipe et est en adéquation avec nos habitudes de développement.

#### Dépendances

Nous utilisons 2 outils de gestion des dépendances sur nos projets : [NPM](https://www.npmjs.com/) et [Bower](http://bower.io/).
Bien que ces deux outils puissent remplir des services similaires, nous les utilisons dans un périmètre précis. 

##### NPM

Les dépendances synchronisées par NPM seront uniquement des outils de déploiements, compilations ou organisations du code existant mais en aucun cas des librairies remplissant un role directement dans le projet.

> Ces dépendances incluent Bower.

Les versions utilisées de ces dépendances sont le plus souvent la dernière disponible mais il est possible que certaines librairies aient de nouvelles version disponibles, charge aux développeur d'effectuer ce genre de vérification en début de projet.

> Le fichier de configuration de NPM `package.json`est un fichier qui sera généré par Stonemason et seules les nouvelles versions ou les librairies additionnelles devront être renseigné.

<br>
L'utilisation de NPM pour définir l'environnement du projet (en développement ou en production selon les besoins) a également l'avantage d'autoriser le lancement de scripts par son intermédiaire. Ainsi, 2 commandes sont référencé par défaut lors de la génération de `package.json` : `start` et `deploy`.

La commande `start` permet d'installer le projet en environnement de développement et s'utilise comme suit :
```bash
npm start
```
La commande `deploy` quant a elle installe le projet en environnement de production : 
```bash
npm deploy
```


##### Bower

Contrairement à NPM, Bower est utilisé uniquement pour les librairies et outils utilisés par le projet. Aucune confusion ne peut être ainsi faite entre les deux gestionnaires de dépendances.

> Le fichier de configuration de Bower `bower.json`est un fichier qui sera généré par Stonemason et seules les nouvelles versions ou les librairies additionnelles devront être renseigné.

<br>

### Utilisation

#### Contenu

L'utilisation des fonctions natives de récupération des données fournies Wordpress peut être d'une grande pénibilité si elle n'est pas bien appréhendé et est généralement peu lisible et donc peu maintenable. Ces raisons ont conduit à la création de plusieurs outils de gestion des données provenant des fonctions embarqué par Wordpress.



#### Ressources

> Les **ressources** comprennent ici tout les documents n'étant pas du code utilisé dans le projet (e.g. images, polices, etc.)

Les ressources sont toutes stockées dans le répertoire suivant : `wp-content/themes/<theme-name>/res/`.
Dans ce répertoire, chacun des type de fichiers seront clairement répartis dans différent répertoires enfants. Ainsi les images seront toutes rassemblé dans le répertoire `wp-content/themes/<theme-name>/res/img/`. Lors de génération du projet par Stonemason, deux répertoires seront créé automatiquement : `img`  et `font`. 

Le répertoire `img` possède deux particularités :
 -  Il contient un répertoire enfant nommé `sprite` destiné à contenir chaque image pouvant être contenu dans un sprite. La création de ce sprite est automatisé par une tâche Grunt.
 - Il ne sera jamais utilisé en production. En effet, une autre tâche grunt va minifier les images et créer un répertoire `public`  dans lequel les fichier réduits seront créés.

Le répertoire `font` ne possède pas de comportement particulier mais par convention, chaque polices ajouté devra être contenue dans un répertoire enfant séparé.

#### Styles

Les règles d'utilisation des feuilles de styles sont définis dans [ce document](https://github.com/Stuff90/Documentation/blob/master/integration/Integration_rules.fr.md).

#### Scripts



#### Templates

#### Taxonomies

#### Filtres
