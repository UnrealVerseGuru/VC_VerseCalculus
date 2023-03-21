## VC - The Verse Calculus - Core Calculus for Functional Logic Programming

**VC** tries to give precise semantics for **Verse Programming Language** (**VPL**) a functional logic language, which is general purpose programming language built directly on VC. VC "_might be a good compiler intermediate language_"(SPJ) and it distills the essence of functional logic programming.

VPL is similar to Icon whereas VC plays the same role as Hanus's _Flat Language FLC_: small core language into which a larger surface language can be desugared.

**1. Prerequisites**
The Paper mainly focues on giving precise syntax for VC with rewrite rules, allowing you to reason about VPL program.

<details>

***<summary>How to reason about VPL - execution & rewrite rules</summary>***
  How one _solves_ this **Verse** program?
  ```
x:tuple(int,int);
x = (2,y:int);
 x = (z:int, 3);
  x
  ```
  You have bunch of Verse code, some instructions which might give you some value, so what to do next ? How to evaluate it's result ?
  This is where VC with it's **rewrite rules** steps in. In math you've learned, you'de have to apply some rules to equation to solve it. There were also some concepts like precedence (firtst multiplication, then addition) and other ideas. This is what this paper mainly tries to do: define **rewrite** rules using simpler, more low level language: VC, which You will apply to Verse program to solve the equation. \
![RewriteRules](https://github.com/UnrealVerseGuru/VC_VerseCalculus/blob/GeneralNotes/Intro/ImageRefs/VC_VerseCalculus_RewriteRulesExmpl.png "Rewrite application example from Haskell")
  
  Paper will give us strategies on when to use certain rewrite rules and those will guide us how to simplify Verse program with VC, eventually solving it. Mentioned later **Confluence** is well illustrated in above example: it's property of rewriting system, describing which terms can be rewritten in more than one way, to yield the same result.
  
--------------------
  
</details>

To understand VC paper one need to accompany himself with many concepts coming from functional logic programming lanugages, be well versed in Lambda Calculus and be aware of research like nature of the paper with many open questions, theories and related works.

Well make shortcuts and focus on findings from VC helping us understanding VPL in this repo.

**To understand VC you must atleast:**
- know **Lambda Calculus**. _Every VC term is Lambda Calculus term and has the same semantics._ <sub>Quote from paper</sub>
- know atleast general info atou Haskell, Prolog, especially differences. Verse being functional logic language shares many concepts of similar languages, and there is abundance of terms from other ones. Knowing them atleast briefly will save you a lot of headaches.

**2. Core syntax**

