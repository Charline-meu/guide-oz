---
title: "Procédures et fonctions"
date: 2021-09-01T20:08:28+02:00
draft: true
---

# Procédures et fonctions

## Procédures
Une procédure est une fonction (au sens d'autres langages) qui **ne retourne rien**.
```oz
proc {ProcedureName Arg1 Arg2}
    {Browse Arg1+Arg2} % Affiche le résultat de Arg1 + Arg2
end
```

## Fonctions
C'est une fonction (au sens d'autres langages) ou une **procédure qui retourne une valeur** (au sens de Oz).
```oz
fun {FunctionName Arg1 Arg2}
    Arg1+Arg2 % Retourne le résultat de Arg1 + Arg2
end
```

## Transformer une fonction en procédure
**Toute fonction est transformable en tant que procédure**. D'ailleurs, dans le **langage noyau de Oz, les fonctions n'existent pas**.
```oz
declare
X
proc {ProcedureName Arg1 Arg2}
    X = Arg1+Arg2
end
{ProcedureName 1 2}
{Browse X} % Affiche 3
```
