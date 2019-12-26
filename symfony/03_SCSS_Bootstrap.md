## SCSS et Bootstrap avec Symfony.
### Installation du module Symfony Encore.
Webpack Encore est une librairie JavaScript permettant d'intégrer simplement Webpack dans ton application, 
Webpack est un outil apportant beaucoup de fonctionnalités pour charger et traiter automatiquement les assets 
```shell
composer require encore
```
### Installation de Yarm dans le projet.
```shell
yarn install
```
### Compilation classique de Webpack (environnement de développement).
```shell
yarn encore dev
```
### Compilation et observation des changements.
```shell
yarn encore dev --watch
```
### Compilation pour un environnement de production.
```shell
yarn encore production
```
### Pour intégrer ces fichiers générés par Encore dans Symfony.
```php
<link rel="stylesheet" href="build/css/app.css"> 
ou 
{% block stylesheets %}
        {{ encore_entry_link_tags('app') }}
{% endblock %}

```
```php
<script src="build/js/app.js"></script>
ou
{% block javascripts %}
           {{ encore_entry_script_tags('app') }}
{% endblock %}
```
### Pour utiliser SCSS dans ton projet.
Il te suffit de décommenter l’option .enableSassLoader() dans le fichier webpack.config.js,
et de rajouter la dépendance dans ton projet.
```shell
yarn add sass-loader@^7.0.1 node-sass --dev
```
### Bootstrap dans un projet symfony.
Style
```shell
yarn add bootstrap --dev
```
Importation
```php
// assets/css/global.scss

// customize some Bootstrap variables
$primary: darken(#428bca, 20%);

// the ~ allows you to reference things in node_modules
@import "~bootstrap/scss/bootstrap";
```
Javascript
```shell
yarn add jquery popper.js --dev
```

```php
// app.js

const $ = require('jquery');
// this "modifies" the jquery module: adding behavior to it
// the bootstrap module doesn't export/return anything
require('bootstrap');

// or you can include specific pieces
// require('bootstrap/js/dist/tooltip');
// require('bootstrap/js/dist/popover');

$(document).ready(function() {
    $('[data-toggle="popover"]').popover();
});
```