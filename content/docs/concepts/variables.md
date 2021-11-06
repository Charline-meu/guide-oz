---
title: "Variables"
date: 2021-09-01T18:40:55+02:00
draft: true
---
# Variables

## Déclarer une variable
Le mot-clé `declare` crée une **variable** et la lie à son **identifiant** (ici `X` et `NumberOfStudents`).
```oz
% Création de la variable x à laquelle on lie l'identifiant X 
% et à laquelle on attribue la valeur 3

declare % Création des variables et liaison à leur identifiant
X = 3 % Affectation
NumberOfStudents = 2 % Affectation
```

### Dans un portée lexicale précise
Le mot clé `local` suivi de `in` et `end` permet de déclarer une variable dans une portée lexicale précise.
```oz
local X in
    X = 3
    {Browse X} % Affiche 3
end
{Browse X} % Erreur car X n'existe pas dans cette portée
```
Un identifiant peut être réutilisé dans une portée lexicale plus petite que la précédente. Si c'est le cas, c'est la valeur la plus locale qui sera utilisée.
```oz
local X in
    X = 3 % X
    {Browse X} % Affiche 3
    local X Y in 
        X = 1 X
        Y = 2 Y
        {Browse X} % Affiche 1
        {Browse Y} % Affiche 2
    end
    {Browse X} % Affiche 3
    {Browse Y} % Erreur car Y n'existe pas dans cette portée
end
```

### Nommage
Les **identifiants** commencent obligatoirement par une **majuscule**.
```oz
declare
NumberOfStudents = 2
```

## Immuabilité
Les variables sont **immuables**. Une fois qu'une valeur leur a été attribué, il est impossible d'en attribuer une nouvelle. Si on essaye tout de même de le faire, l'analyse statique nous empêchera de le faire.
```oz
declare
X = 20
X = 10 % L'analyse statique se plaint ici de la tentative de réaffectation
```

## Typage dynamique
Le **type** d'une variable est connu seulement **à l'affectation** (typage dynamique).
```oz
declare
X % Pas de type
X = 10 % Int
```
