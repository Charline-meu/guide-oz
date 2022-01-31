---
title: "Macos"
date: 2021-08-24T14:21:38+02:00
draft: false
---
# MacOS

## Prérequis

### Homebrew
Rendez-vous sur le site de [Homebrew](https://brew.sh/) et **suivez les instructions d'installation** disponibles sur la page d'accueil du site. Toutes les commandes qui suivent utilisent `Homebrew` donc vous devez l'installer en premier.

### Emacs
N'importe quelle version d'`Emacs` fera l'affaire cependant le professeur recommande `Aquamacs`.

#### Aquamacs
```shell
brew install --cask aquamacs
```

## Installation

D'abord, **clonez le répertoire qui contient Mozart2** en tapant la commande suivante dans votre terminal:
```shell
brew tap dskecse/tap
```
Ensuite, **installez Mozart2** avec la commande suivante:
```shell
brew install --cask mozart2
```
Une application se nommant `Mozart2` devrait à présent se trouver dans votre dossier `Applications`. Si MacOs vous empêche de la lancer, ouvrez Finder et **cliquez droit sur l'application** puis **cliquez sur ouvrir**.

Une version d'Emacs configurée pour Mozart2 devrait alors s'ouvrir. Amusez-vous bien!