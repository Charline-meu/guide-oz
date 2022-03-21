---
title: "Séance 5"
date: 2022-03-01T12:10:21+01:00
draft: false
weight: 5
---

# Séance 5

## Question 1
    1. [X] λx.xyz
    2. [ ] λx.λy
    3. [X] m
    4. [X] xλwy.y
    5. [ ] xλ
    6. [ ] λλxz.zx
    7. [X] (mnop)(qrst)vwλxyz.zxy

## Question 2
    1. (λx(λy.x))
    2. (λx(λx.x))
    3. (λx.x(λy.x))
    4. (λx.x(λx.x))
    5. (λz.x(λy.x))
    6. (λz.x(λx.x))

## Question 3
    1. [X] λa.λb.abb λb.λa.baa
    2. [ ] λa.λb.λa.bb λi.λj.jji
    3. [ ] λx.xλy.x λe.eλf.f
    4. [X] λx.xλy.x λe.eλf.e

## Question 4
    1. yy
    2. ayya
    3.  - (λx.(λz.zx)q)y
        - (λz.zy)q
        - qy
    4.  - (λx.x((λz.zx)(λx.bx)))y
        - y((λz.zy)(λx.bx))
        - y(y(λx.bx))
        - y(by)
    5.  - (λm.m)(λn.n)(λc.cc)(λd.d)
        - (λm.m)(λn.n)(λc.(λd.d)(λd.d))
        - (λm.m)(λn.(λc.(λd.d)(λd.d)))
        - (λm.λn.λc.(λd.d)(λd.d)))
        - (λd.(λd.d))
        - (λd.d)
    6.  - λz.xλx.x

## Question 5
    1.  - λx.(λy.y)x
        - λy.y
    2.  - λx.(λy.(λz.p)y)x
        - λy.(λz.p)y
        - λz.p
    3.  - λx.(λy.(λz.z))x
        - λy.(λz.z)
    4.  - λx.(λy.yx)p
    5.  - (λf.fx)(λy.gy)
        - (λy.gy)x
        - (λf.fx)g

## Question 6
    1.1 - (λx. λy. x) ((λx. x) y)
        - (λx.λy. x) (λy. y)
        - (λx. x) (λy. y)
        - λy. y

    1.2 - (λx. λy. x) ((λx. x) y)
        - λy.(λx. x)y
        - λy. y

    2.1 - (λx.λy. xy) (λz. z) (λw. w)
        - (λy. (λw. w)y) (λz. z)
        - (λw. w)(λz. z)
        - (λw. w)

    2.2 - (λx.λy. xy) (λz. z) (λw. w)
        - (λx. x(λz. z))(λw. w)
        - (λw. w)(λz. z)
        - λz.z

## Question 7
    NOT ≜ λp.p false true
    OR ≜  λp.λq p p q
    OR TRUE FALSE ≜ (λp.λq.p) true false

## Question 8
    SUCC ≜ λn.λf.λx.f (n f x)

## Question 9
    FIRST ≜ λp.p true
    FIRST ≜ λa.λb. a

    SECOND ≜ λp.p false
    SECOND ≜ λa.λb. b

    PAIR ≜ λx.λy.λf.f x y
    λf.f 4 2
    FIRST -> true 4 2 -> 4
    SECOND -> false 4 2 -> 2

    List ≜ λf.f h t

## Question 10

## Question 11

## Question 12
