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

<details>

***<summary>few Lambda Calculus tenets</summary>***
  
An expression $\lambda (x.E) M$ is called a **redex** (for reducible expression)
  
A reduction strategy (also called evaluation order) is a strategy for choosing redexes:
  * ***Applicative order reduction*** (**call-by-value**) **Strict evaluation strategy** is an eager evaluation strategy: chooses the ***leftmost-innermost*** redex in an expression
  * ***Normal order reduction*** (**call-by-name**) **lazy evaluation strategy** - chooses the ***leftmost-outermost*** redex in an expression
  * **Church-Rosser Theorem**: Normal form implies that there are no more reductions possible (since that arriving at same result using both strategies not always the case)
    * If normal form exists, then it is unique (i.e., result of computation does not depend on the order that reductions are applied; i.e., no expression can have two distinct normal forms)
    * If normal form exists, then normal order will find it
  
 ----------------------
 
 </details>

**2. Core syntax & tenets**

1. Pay attention to spacing. Very important in Lambda Calculus & VC as parentheses _()_ are often optional or used to force evaluation in different way
2. Desugaring simply means simplifying Verse code with use of VC
3. We use the symbol “≡” to indicate that when A ≡ B, A is just a synonym of B.
4. Form: **Fig 1.** will concern images copied from the paper

![RewriteRules](https://github.com/UnrealVerseGuru/VC_VerseCalculus/blob/GeneralNotes/Intro/ImageRefs/VC_AbstractSyntax1.png "Rewrite application example from Haskell")
#### Values _v_
  * either variable _x_
  * or head-normal form: _hnf_ which is either conventional value:
    *  built-in integer constant _k_. Integer is number that can be positive, negative, or zero, and is not a fraction or a decimal e.g. _12345_, _999_, _0_
    *  operator _op_ integers operators **gt** and **add**
    *  tuple (a pair). Very important in VC, those are data constructors
    *  lambda $\lambda$ (from Lambda Calculus: symbol indicating starting of definition of a function)

#### Expressions _e_
  * values _v_
  * application $v_1 v_2$
    * For clarity often $v_1 (v_2)$ used when $v_2$ is not a tuple
    * formal syntax for e allows only applications of _values_, $v_1 (v_2)$, but the desugaring rules show how to desugar more applications $e_1 (e_2)$

#### Term _eq_
  * Ordinary expression _e_
  * equation _v=e_
    * equations can only occur to the left of ";"

#### Logical variables and equations that constrain their values
  * to bring a fresh logical variable into scope use ∃
  * to constrain a value to be equal to an expression with an equation use $v=e$
  * to compose expressions in sequence use $𝑒𝑞; e$
  * **Equation:** syntax carefully constrains both the form of equations and where they can appear: an equation $(v=e)$ always equates a value 𝑣 to an expression 𝑒; and an equation can only appear to the left of a “;”
    *  The desugaring rules in Fig. 1 rewrite a general equation $e1=e2$ into this simpler form

#### _program_ _p_
  * contains closed expression from which result gets extracted using **one**, unless the expression fails, in which case the program fails
  * A program executes by solving its equations, using the process of unification



<!-- 
    in VC every variable is a function, we use $\lambda$ to define a function just as in LC which is called Lambda Abstraction

# ![RewriteRules](LINK "Rewrite application example from Haskell")
