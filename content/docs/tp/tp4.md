---
title: "Séance 4"
date: 2022-02-22T15:40:34+01:00
draft: false
weight: 4
---

# Séance 4

## Question 1
- cf. Slide 4-6 cours 4

## Question 2
```oz
declare 
fun {MakeMulFilter N}
   fun {$ I} I mod N == 0 end 
end

fun {IsPrime N} 
    fun {IsPrimeAcc N Acc} 
        if N =<1 then false 
        elseif N==Acc then true 
        else 
            if {{MakeMulFilter Acc} N} then false 
            else {IsPrimeAcc N Acc+1} 
            end 
        end 
    end 
in 
    {IsPrimeAcc N 2} 
end

fun {Filter L F}
    fun {FilterAcc L F Acc}
        case L of nil then Acc
        [] H|T then 
            if {F H} then {FilterAcc T F H|Acc}
            else {FilterAcc T F Acc}
            end
        end
    end
in
    {FilterAcc L F nil}
end

Digits = [0 1 2 3 4 5 6 7 8 9]
MultipleOf2 = {MakeMulFilter 2}
MultipleOf3 = {MakeMulFilter 3}

% Le résultat est dans l'ordre inverse parce que j'ai utilisé un accumulateur
% Vous pouvez soit ne pas en utiliser, soit faire un {List.reverse L} pour ravoir le bon ordre
% Ici on ne précisait pas de garder l'ordre donc je ne me suis pas tracassé
{Browse {Filter Digits MultipleOf2}}
{Browse {Filter Digits MultipleOf3}}
{Browse {Filter Digits IsPrime}}
```

## Question 3
```oz
declare 
fun {FoldL L F A}
    case L of nil then A
    [] H|T then {FoldL T F {F H A}}
    end
end

fun {MultiplyList L}
    {FoldL L fun {$ X Y} X*Y end 1}
end

fun {SubstractList L}
    {FoldL L fun {$ X Y} Y-X end 0}
end

Digits = [1 2 3 4 5 6 7 8 9]
Brr = [1 2 3 4]
{Browse {MultiplyList Digits}}
{Browse {DiffList Brr}}
```

## Question 4
```oz
declare 
fun {Applique L F} 
   case L of nil then nil 
   [] H|T then {F H}|{Applique T F}
   end 
end 

fun {Pow N E} 
   fun {Pow N E Acc}
      case E of 0 then Acc
      else {Pow N E-1 N*Acc} 
      end 
   end
in
   {Pow N E 1}
end 

fun {PowE E} 
   fun {$ N} 
      {Pow N E} 
   end 
end

fun {PowList L E} 
   {Applique L {PowE E}} 
end 

{Browse {PowList [1 2 3] 2}} 
```

## Question 5
```oz
declare
fun {Convertir T V}
   T*V
end

fun {ConvertirBetter T}
   fun {$ V}
      T*V
   end
end

fun {ConvertirBetter2 A B}
   fun {$ V}
      A*V+B
   end
end


PiedVersMetre = {ConvertirBetter 0.30480370641307}
FarenheitToCelcius = {ConvertirBetter2 0.56 ~17.78}
{Browse {PiedVersMetre 3.0}}
{Browse {FarenheitToCelcius 3.0}}
```

## Question 6
```oz
declare
fun {PipeLine N}
   P1 P2 P3 in
   P1 = {GenerateList N}
   P2 = {MyFilter P1 fun {$ X} X mod 2 \= 0 end}
   P3 = {MyMap P2 fun {$ X} X * X end}
   {MyFoldL P3 fun {$ Acc X} X + Acc end 0}
end

fun {GenerateList N}
   fun {GenerateListAcc N Acc} 
      case N of 0 then Acc
      else {GenerateListAcc N-1 N|Acc}
      end
   end 
in 
   {GenerateListAcc N nil} 
end

fun {MyFilter L F}
   fun {FilterAcc L F Acc}
       case L of nil then Acc
       [] H|T then 
           if {F H} then {FilterAcc T F H|Acc}
           else {FilterAcc T F Acc}
           end
       end
   end
in
   {FilterAcc L F nil}
end

fun {MyMap L F} 
   fun {MyMapAcc L F A}
      case L of nil then A
      [] H|T then {MyMapAcc T F {F H}|A}
      end
   end
in
   {MyMapAcc L F nil}
end 

fun {MyFoldL L F Acc} 
   case L 
   of nil then Acc
   [] H|T then {MyFoldL T F {F Acc H}}  
   end 
end 

{Browse {PipeLine 10}}
```

## Question 7
```oz
local Y LB in
   Y=10
   proc {LB X ?Z}
      if X>=Y then Z=X
      else Z=Y end
   end
   local Y=15 Z in
      {LB 5 Z}
      % Affiche 1O car le Y utilisé par LB est celui
      % de son contexte pas de celui où LB est appelé
      {Browse Z} 
   end
end
```
