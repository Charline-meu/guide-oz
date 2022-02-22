---
title: "Séance 3"
date: 2022-02-15T11:29:43+01:00
draft: false 
---

# Séance 3

## Question 1
### Partie 1
```oz
declare
proc {SumKernel N ?R}
   local One NEqualsOne in
      One = 1
      NEqualsOne = (N == One)
      if NEqualsOne then R = One
      else 
         local V NMinusOne NTimesN in
            NMinusOne = N-One
            NTimesN = N*N
            {SumKernel NMinusOne V}
            R = NTimesN + V
         end
      end
   end
end

A
{SumKernel 10 A}
{Browse A}
```
### Partie 2
```oz
declare
proc {SumAuxKernel N Acc ?R}
   local One NEqualsOne in
      One = 1
      NEqualsOne = (N==One)
      if NEqualsOne then R = Acc + One
      else
         local NMinusOne NTimesN NewAcc in
            NMinusOne = N - One
            NTimesN = N * N
            NewAcc = NTimesN + Acc
            {SumAuxKernel NMinusOne NewAcc R}
         end
      end
   end
end

proc {SumKernel N ?R}
   {SumAuxKernel N 0 R}
end
A
{SumKernel 10 A}
{Browse A}
```
Cette fonction est résurvive terminale

## Question 2
```oz
declare
A = '|'(1:1 2:nil)
B = '|'(1:1 2:'|'(1:2 2:'|'(1:3 2:nil)))
C = nil
D = state(1:4 2:f 3:3)

{Browse A}
{Browse B}
{Browse C}
{Browse D}
```

## Question 3
```oz
proc {Q A} {P A+1} end
% Ec = {P -> p}

proc {P} {Browse A} end
% Ec = {Browse->browse, A -> a}

local P Q in
   proc {P A R} R=A+2 end
   % Ec = {}

   local P R in
      fun {Q A}
         {P A R}
         R
      end
      % Ec = {R -> r, P -> p}

      proc {P A R} R=A-2 end
      % Ec = {}
   end
end
```
