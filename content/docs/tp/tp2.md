---
title: "Séance 2"
date: 2022-02-09T10:00:46+01:00
draft: true
weight: 2
---
# Séance 2

## Question 1
```oz
declare
% Définitions
L1 = a|nil
L2 = a|(b|c|nil)|d|nil
L3 = proc {$} {Browse oui} end|proc{$} {Browse non} end|nil
L4 = est|une|liste|nil
L5 = (a|p|nil)|nil

% Nouvelle list en ajoutant ceci
NewList = ceci|L4

% Appel de la première procédure
{L3.1}

% Obtention de [[b c] d]
End = L2.2

% Fonction head et tail
fun {Head L}
    case L of H|_ then H 
    else nil end
end

fun {Tail L}
    case L of _|T then T
    else nil end
end
```

## Question 2
```oz
declare
fun {Length L}
    fun {LengthAcc L Acc}
        case L of nil then Acc
        [] _|T then {LengthAcc T Acc+1}
        end
    end
in
    {LengthAcc L 0}
end
```

## Question 3
```oz
declare
fun {Append L1 L2}
   case L1 of H|T then H|{Append T L2}
   [] nil then L2
   end
end
```

## Question 4
```oz
declare
fun {IsEmpty L}
    case L of nil then empty
    [] _|_ then nonEmpty
    else other end
end
```

## Question 5
```oz
declare
fun {Take Xs N}
   case Xs of H|T then
      if N>0 then H|{Take T N-1}
      else nil end
      [] nil then nil
   end
end

fun {Drop Xs N}
   case Xs of H|T then
      if N>0 then {Drop T N-1}
      else Xs
      end
   [] nil then nil
   end
end
```

## Question 6
```oz
declare
fun {MultList L}
    fun {MulListAcc L Acc}
        case L of nil then Acc
        [] H|T then {MulListAcc T H*Acc}
        end
    end
in
    {MulListAcc L 1}
end
```

## Question 7
```oz
declare
L1 = [[1 2 3] [4 5 6]]
L2 = (1|2|3|nil)|(4|5|6|nil)|nil
L3 = (1|(2|(3|nil)))|(4|(5|(6|nil)))|nil
```

## Question 8
```oz
declare
fun {Prefix L1 L2}
   case L1 of H1|T1 then
        case L2 of H2|T2 then
	        if H1 == H2 then {Prefix T1 T2}
	        else false
	        end
        [] nil then false
        end
    [] nil then true
    end
end

fun {FindString S T}
    IndexMax = {Length T} - {Length S} + 1
    fun {FindStringHelp L1 L2 I}
        if I =< IndexMax then
            if {Prefix L1 L2} then
                I|{FindStringHelp L1 L2.2 I+1}
            else {FindStringHelp L1 L2.2 I+1}
            end
        else nil
        end
    end
in
    {FindStringHelp S T 1}
end
```

## Question 9
```oz
declare
Carte = carte(menu(entree: 'salade verte aux lardons'
		   plat: 'steak frites'
		   prix: 10)
	      menu(entree: 'salade de crevettes grises'
		   plat: 'saumon fume et pommes de terre'
		   prix: 12)
	      menu(plat: 'choucroute garnie'
		   prix: 9))

{Browse Carte.2} % Second menu
{Browse Carte.2.plat} % Plat second menu
{Browse Carte.1.entree} % Entree second menu
% Ce sont des string. Des listes d'entiers inteprétés comme des char.

% Permet de calculer le prix si N1 personnes prennent le menu 1 etc
fun {GetPrice C N1 N2 N3}
   N1 * C.1.prix + N2 * C.2.prix + N3 * C.3.prix
end

% Arité de la carte 3 et celle des menus 3 aussi je dirais
```

## Question 10

## Question 11
```oz
declare
fun {DictionnaryFilter D F}
   case D of dict(key: Key info: Info left: Left right: Right) then
	    if {F D.info} then Key#Info|{DictionaryFilter Left F}|{DictionnaryFilter Right F}
	    else {DictionaryFilter Left F}|{DictionaryFilter Right F}
	    end
	 [] leaf then nil
   end
end

local Class Old Value in
    Class = dict(key:10
                info:person('Christian' 19)
                left:dict(key:7
                    info:person('Denys' 25)
                    left:leaf
                    right:dict(key:9
                        info:person('David' 7)
                        left:leaf
                        right:leaf))leaf
                right:dict(key:18
                    info:person('Rose' 12)
                    left:dict(key:14
                        info:person('Ann' 27)
                        left:leaf
                        right:leaf)
                    right:leaf))

    fun {Old Info}
        Info.2 > 20
    end
    % Val --> [7#person('Denys' 25) 14#person('Ann' 27)]
    {Browse {DictionaryFilter Class Old }}
end
```
## Question 12
```oz
{Browse {IsTuple '|'(a b)}} %->true, not a list 

{Browse {IsTuple state(1 a 2)}} %->true, not a list 

{Browse {IsTuple a#b#c}} %->true 

{Browse {IsList '|'(a '|'(b nil))}} %->true 

{Browse {IsTuple state(1 3:2 2:a)}} %->true, not a list, even if fields not in order 

{Browse {IsList [a b c]}} %->true 

{Browse {IsList '|'(2:nil a)}} %->true 

{Browse {IsTuple tree(v:a b c)}} %->false, it is a record 

{Browse {IsTuple m|n|o}}%->true, not a list
```

## Question 13
```oz
declare
fun {Applique L F}
   case L of H|T then {F H}|{Applique T F}
   [] nil then nil
   end
end

fun {Lol X} lol(X) end
{Browse {Applique [1 2 3] Lol}}


fun {MakeAdder N}
   fun{$ X}
      X+N
   end
end

Add5 = {MakeAdder 5}
{Browse {Add5 13}}


fun {AddAll L N}
    Add = {MakeAdder N}
in
    {Applique L Add}
end
{Browse {AddAll [1 2 3] 4}}
```

## Question 14