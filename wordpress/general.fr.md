# Wordpress

L'utilisation de Wordpress est souvent nécessaire pour de nombreux projets. Cependant, le moteur de blog n'est pas toujours pertinent dans sa version de base. De nombreux outils et règles d'utilisations ont donc été mis en place.

### Index

 1. [Installation](#installation)
  - [Wordpress](#wordpress)
  - [Dépendances](#dépendances)
  - [Outils de développement](#outils-de-développement)
  - [Outils d'intégration](#outils-dintégration)
 2. [Utilisation](#utilisation)
  - [Contenu](#contenu)
  - [Ressources](#ressources)
  - [Styles](#styles)
  - [Scripts](#scripts)
  - [Templates](#templates)
  - [Taxonomies](#taxonomies)
  - [Filtre](#filtre)

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

> Le fichier de configuration de NPM `package.json`est un fichier qui sera généré par Stonemason et seuls les nouvelles versions ou les librairies additionnelles devront être renseigné.

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

#### Outils de développement

#### Outils d'intégration

### Utilisation

#### Contenu

#### Ressources

#### Styles

#### Scripts

#### Templates

#### Taxonomies

#### Filtre

