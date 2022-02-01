---
title: "Séance 1"
date: 2022-02-01T14:31:20+01:00
draft: true
---
# Séance 1

## Question 1
```oz
% Exécutez le programme en utilisant "Feed Region" pour le bloc code
% Ou "Feed Line" pour la ligne de code
{Browse 1}
{Browse 2}
{Browse 3}
{Browse 4}
```

## Question 2
```oz
{Browse 19 - 970}
{Browse 192 - 980 + 191*967}
{Browse (192-780)*(~3) - 191*967}
```

## Question 3
```oz
% On ne peut pas utiliser les types flottants et entiers ensemble
% en oz donc on doit les convertir pour faire des opérations
{Browse 123 + {FloatToInt 456.0}}
{Browse {IntToFloat 123} + 456.0}
```

## Question 4
De simples exemples :
```oz
declare
X = 19
Y = 970

{Browse X+Y}
```

```oz
% X et Y sont utilisables entre le local et le end
local X Y in
    X = 19
    Y = 970
    {Browse X+Y}
end
```

## Question 5

## Question 6

## Question 7
```oz
declare
fun {SignOfInteger X}
    if X == 0 then 0
    elseif X > 0 then 1
    else ~1 end
end
```

## Question 8
```oz
local P Q X Y Z in % (1)
    local Y in % Premier changement
        Y=X
        fun {P X}
            X*Y+Z % (2)
        end
    end

    local Z in % Second changement
        Z = Y
        fun {Q Y}
            X*Y+Z % (3)
        end
    end

    X=1
    Y=2
    Z=3
    {Browse {P 4}}
    {Browse {Q 4}}
    {Browse {Q {P 4}}} % (4)
end
```

## Question 9

## Somme des carrés
```oz
declare
fun {SquareSum X}
    {SquareSumAux X 0}
end

fun {SquareSumAux X Acc}
    if X == 0 then Acc
    else {SquareSum X-1 Acc+X*X} end
end

{Browse {SquareSum 6}}
```

Autre synthaxe que vous verrez plus tard mise ici pour l'exemple.
```oz
declare
fun {SquareSum X}
    fun {SquareSumAux X Acc}
        if X == 0 then Acc
        else {SquareSumAux X-1 Acc+X*X} end
    end
in
    {SquareSumAux X 0}
end

{Browse {SquareSum 6}}
```

## Miroir, mon beau miroir...
```oz
declare
fun {Miror N}
   {MirorAux N 0}
end

fun {MirorAux N I}
   if N==0 then I
   else {MirorAux (N div 10) I*10+N mod 10} end
end

	
{Browse {Miror 146587234}}
```

## Univers parallèle
### Partie 1
### Partie2

## Un, deux, trois, nous irons au bois
```oz
declare
proc {Countdown N}
   if N == 0 then {Browse 0}
   else {Browse N} {Countdown (N-1)}
   end
end
{Countdown 5}
```