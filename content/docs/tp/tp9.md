---
title: "Séance 9"
date: 2022-03-28T14:32:38+02:00
draft: true
---

# Séance 9

## Exercice 1

## Exercice 2

## Exercice 3
```oz
declare

fun {MakeBinaryGate F}
    fun {$ S1 S2}
        fun {Gate SA SB}
	        case SA#SB
            of (HA|TA)#(HB|TB) then
                {F HA HB}|{Gate TA TB}
            else
                nil
            end
        end
    in
        thread {Gate S1 S2} end
    end
end

And = {MakeBinaryGate fun {$ A B} A*B end}
Or = {MakeBinaryGate fun {$ A B} A+B-A*B end}
Nand={MakeBinaryGate fun {$ X Y} 1-X*Y end}
Nor={MakeBinaryGate fun {$ X Y} 1-X-Y+X*Y end}
Xor={MakeBinaryGate fun {$ X Y} X+Y-2*X*Y end}
S1 = 0|0|1|1|_
S2 = 0|1|0|1|_
```

## Exercice 4
```oz
local R=1|1|1|0|_ S=0|1|0|0|_ Q NotQ
   fun {Delay S}
      0|S
   end

   proc {Bascule Rs Ss Qs NotQs}
      DelayedQs = {Delay Qs}
      DelayedNotQs = {Delay NotQs}
   in
      {Nor Rs DelayedNotQs Qs}
      {Nor Ss DelayedQs NotQs}
   end
in
   {Bascule R S Q NotQ}
   {Browse Q#NotQ}
end
```