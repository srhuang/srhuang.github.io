---
layout: post
comments: true
mathjax: true
title: "快速了解 Formal Language (形式語言)"
categories:
  - Formal Language
tags:
  - theory
  - mathematics
---

這篇文章只會簡單的介紹 formal language，目的是用最快的速度擁有最粗淺的了解，如果對於這個領域還有興趣，可以再分項一一往下研究。
Turing Machine 在 1936 年由 Alan Turing 提出後，便奠定了現今電腦的基礎，整個 Formal Language 大約是在 1930-1940 年代發展成熟，而人類第一台通用計算機 [ENIAC](https://zh.wikipedia.org/wiki/%E9%9B%BB%E5%AD%90%E6%95%B8%E5%80%BC%E7%A9%8D%E5%88%86%E8%A8%88%E7%AE%97%E6%A9%9F) 則是 1946 的事情了。

<!--more-->

## Overview
* [Definition : Languages, Grammars, Automata](#Definition)
* [Regular Languages and DFA](#Regular)
* [Context-Free Languages and Pushdown Automata](#CFL)
* [Recursively enumerable Languages and Turing Machine](#REL)
* [Context-Sensitive Languages and Linear Bounded Automata](#CSL) 
* [The Chomsky Hierarchy](#Chomsky)
* [Limits of Algorithmic Computation](#limits)
* [Computational Complexity](#complexity)

## Why we study formal language theory?
>theory provides concepts and principles that help us understand the general nature of the discipline.

學習理論讓我們知道計算機科學的最核心的概念和原則，進而了解電腦的極限，而不用透過無意義的 trial-and-error 以及猜測來理解電腦，以更高的角度來看待計算機科學。

>the ideas we will discuss have some immediate and important applications.e.g. digital design, programming languages, and compilers.

就實作面來說，formal language 是 compiler 的理論基礎，因為 compiler 就是在處理語言和字串，本質上和 formal language 所探討的問題是一致的；programming languages 核心的概念也是把人類理解的語言，轉成機器可以執行的語言，不論高階語言還是低階語言，本質上都是處理語言和字串的轉換。

>the subject matter is intellectually stimulating and fun.

最後一個理由是，透過理解這些理論基礎和證明，會再次感受到前人研究的偉大，而我們也只是站在這些巨人的肩膀上，希望獲得新知識的過程能帶來無比的成就感以及樂趣。

Using Formal Language : 
* definition of programming languages.
* interpreters.
* compilers.

<details>
    <summary>關於 formal language 的翻譯
</summary>
如果把 formal language 翻譯成「正規語言」，那 regular language 可能會不知道該如何翻譯，因此比較好的翻譯應該是「形式語言」，而「正規語言」是包含於「形式語言」。
</details>

## <a id="Definition"></a>Definition : Languages, Grammars, Automata
在開始討論 formal language 之前，我們必須對於要討論的對象做根本上的定義。

*Languages* 是一個數學上的字串集合；
這些字串集合的 derivation rules 就稱為 *Grammars*；
而設計一個自動機來決定給定的字串是否屬於該集合則稱為 *Accepter* (Automata 的一種)。


**Languages** 的例子：
$$ L_1=\{ a^nb^n : n \geq 0 \} $$

**Automata** 基本上分為兩種：
* Accepter : output response is limited to a simple “yes” or “no”.
* Transducer : producing strings of symbols as output.

**Grammars** 是用數學嚴謹的定義來描述 language：
* variables (V) : finite set.
* terminal symbols (T) : finite set.
* start variable (S) : special symbol.
* productions (P) : which used to derives the strings.

$$ 
G_1 = (\{A,S\},\{a,b\},S,P_1)\ with\ P_1\ consisting\ of\ the\ productions \\
S \to aAb|\lambda \\
A \to aAb|\lambda
$$

這個 Grammar 其實就是 Language $L_1$ 那個例子的 Grammar，所以 $$L(G_1) = L_1$$。

## <a id="Regular"></a>Regular Languages and DFA
我們將會從最簡單的 automata 開始討論，由於接下來的 automata 都是 accepters，所以可以暫時理解 $automata=accepters$。

Language 是一種字串的集合，關於這個集合我們會用各種角度和方式來描述它，讓它變得更加具體，其中一個就是設計一個 automata 讓所有該集合的字串都能通過該 automata(accepter)；Grammars 則是透過數學的方式來描述該 language。

### Finite Automata (Finite State Machine, FSM)
* Deterministic Finite Automata (DFA) is defined by internal states, input alphabet, transition function, initial state, final states.
    * each move consumes one input symbol.
    * the string is accepted if the automaton is in one of its final states.

* Nondeterministic Finite Automata (NFA)
    * transition function range is a set of possible states.
    * can make a transition without consuming an input symbol.
    * there is no transition defined for the specific situation.

>The classes of DFA and NFA are equally powerfully.

### Regular Language
A language $L$ is called regular if and only if there exists some DFA $M$ such that, $L=L(M)$.

### Regular Grammar
* A language $L$ is regular if and only if there exists a regular grammar $G$ such that $L=L(G)$.
* A regular grammar is one that is either right-linear or left-linear, which there is exactly one variable occuring as the rightmost/leftmost symbol.\\
Right-Linear Grammars ：$A \to xB$\\
Left-Linear Grammars : $A \to Bx$

### Regular Expression
* One way of describing regular language is via the notation of regular expression.
* Two regular expressions are equivalent if they denote the same language.

>There are three ways to describe regular languages：DFA, regular expression, regular grammars.

<details>
    <summary>想知道更多？
</summary>
<ul>
  <li>Closure Properties of Regular Languages</li>
  <li>membership algorithm</li>
  <li>Identifying Nonregular Languages
    <ul>
        <li>Pigeonhole Principle (鴿籠原理)</li>
        <li>Pumping Lemma</li>
    </ul>
  </li>
</ul>
</details>

## <a id="CFL"></a>Context-Free Languages and Pushdown Automata
雖然 regular language 廣泛應用在 computer science 領域中，但是還是有很多是 regular language 無法處理的，例如我們舉的第一個例子：

$$ L_1=\{ a^nb^n : n \geq 0 \} $$

假如 $a=“(”, b=")"$，那麼這個 language 所產生的 automata 將會是判斷 programming language 的括號是否合法的方法之一。可以想像的是，利用 finite state 將無法紀錄已經 parsing 幾個 a 了，因此我們需要更強大的 language 來處理 regular language 無法處理的 language。
最核心的概念就是在 finite state 以外新增 storage (stack)。你將會發現「新增/修改 storage」是區別每個 language 所對應的 automata 重要的 property 之一。

### Context-Free Grammars
* all productions in P have the form $A \to x$.
* retaining the restriction on the left side, but permitting anything on the right.

### Context-Free Languages
* A language $L$ is said to be context-free if and only if there is a context-free grammar $G$ such that $L=L(G)$.

<details>
    <summary>想知道更多？
</summary>
<ul>
  <li>Derivation Tree (Parse tree)</li>
  <li>Sentential form of the derivation</li>
  <li>Parsing and Ambiguity
    <ul>
        <li>exhaustive search parsing (brute force parsing)</li>
        <li>Simple Grammar (s-grammar)</li>
    </ul>
  </li>
  <li>Simplification of Context-Free Grammars and Normal Forms
    <ul>
        <li>Chomsky Normal Form : A->BC or A->a</li>
        <li>Greibach Normal Form : A->ax</li>
    </ul>
  </li>
</ul>
</details>

### Pushdown Automata
* Nondeterministic Pushdown Automata (NPDA)
    * For any context-free language $L$, there exists an NPDA $M$ such that $L=L(M)$.
    * If $L=L(M)$ for some NPDA $M$, then $L$ is a context-free language.
* Deterministic Pushdown Automata (DPDA)
    * A language $L$ is said to be a deterministic context-free language if and only if there exists a DPDA $M$ such that $L=L(M)$.

>deterministic and nondeterministic pushdown automata are not equivalent.

<details>
    <summary>想知道更多？
</summary>
<ul>
  <li>Properties of Context-Free Languages
    <ul>
        <li>A pumping lemma for context-free languages</li>
        <li>Closure Properties for Context-Free Languages</li>
    </ul>
  </li>
</ul>
</details>

## <a id="REL"></a>Recursively enumerable Languages and Turing Machine
我們發現還是有 Language 不屬於 regular and context-free language

$$ L_1=\{ a^nb^nc^n : n \geq 0 \} $$

因此透過修改 storage 可以得到更 powerful 的 language : Turing Machine (Using Tapes).

### Turing Machine
* Definition : associated with the tape is a read-write head that can travel right or left.
* The Turing machine enters a final state and halts, then the string is considered to be accepted.
* main features : 
    * tape is unbounded in both directions.
    * deterministic.
    * no special input file / output device.
* Church Turing Thesis : 任何在算法上可計算的問題同樣可由圖靈機計算。

### Recursively enumerable Languages
* A language $L$ is said to be recursively enumerable if there exists a Turing machine that accepts it.
* There is an *enumeration procedure* for every recursively enumerable language.
* enumeration procedure : 存在一個 algorithm 可以列出所有 strings in the language.
* Recursively enumerable Languages is countable.

### Recursive Languages
* A language is recursive in and only if there exists a *membership algorithm* for it.
* membership algorithm : 存在一個 algorithm 可以決定該 string 是否屬於 language。
* If a language is recursive, then there exists an enumeration procedure.

>* the family of recursive language is a proper subset of the family of recursively enumerable languages.

<details>
    <summary>想知道更多？
</summary>
<ul>
  <li>這邊常用的證明方法 : diagonalization</li>
</ul>
</details>

### Unrestricted Grammars
* A grammar is called unrestricted if all the productions are of the form $u \to v$.
* Any number of variables and terminals can be on the left or righting any order.
* Any language generated by an unrestricted grammar is *recursively enumerable*.
* For every recursively enumeration language $L$, there exists an unrestricted grammar $G$, such that $L=L(G)$.

## <a id="CSL"></a>Context-Sensitive Languages and Linear Bounded Automata
Context-free languages，顧名思義就在 derivation 的時候並不考慮上下文，因此根據 definition，there is no terminal on the left of any production.接下來將會介紹根據上下文的 Context-Sensitive Languages。

### Context-Sensitive Grammars
* A grammar is called Context-Sensitive if all the productions are of the form $x \to y$, where $$\|x\| \leq \|y\|$$.
* the length of successive sentential forms can never decrease.

### Linear Bounded Automata
* Turing machine with limiting the tape.
* For every context-sensitive language $L$ (not including empty string), there exists some linear bounded automata $M$ such that $L=L(M)$.

### Context-Sensitive Languages
* A language $L$ is said to be context-sensitive if and only if there is a context-sensitive grammar $G$ such that $L=L(G)$.

## <a id="Chomsky"></a>The Chomsky Hierarchy
* Type 0 : recursively enumerable languages (unrestricted grammars).
* Type 1 : context-sensitive language.
* Type 2 : context-free language.
* Type 3 : regular language.

<details>
    <summary>想知道更多？
</summary>
<ul>
  <li>Recursive Languages</li>
  <li>Linear Languages</li>
  <li>Determinitstic Context-Free Languages</li>
</ul>
</details>

## <a id="limits"></a>Limits of Algorithmic Computation
>Computable Functions : It states that a function on the natural numbers can be calculated by an effective method, if and only if it is computable by a Turing machine.

接下來，我們將會討論那些 Turing machine 無法處理的問題，在討論之前，先介紹幾個概念。

### Computability
>A function $f$ is said to be computable if there exists a Turing Machine that computes the value of $f$.

### Decidability
>The result of a computation is simple “yes” or “no”, in this case, a problem being decidable or undecidable.

#### The Turing Machine Halting Problem
「給定一個 input string 和 Turing Machine，把 string 丟進去 Turing Machine 執行後是否會停在某個 state，抑或是執行後永不停止。」

這個問題是 undecidable，證明方法主要是利用反證法：If halting problem were decidable, then every recursively enumerable language would be recursive. 因為如果知道會不會停止，就可以建構出 membership algorithm，而凡是可以建構出 membership algorithm 的 language 就是 recursive language。

可以 reduced to Halting Problem 的問題：
* The state-entry Problem : the state is ever entered when applied to input string.
* The blank-tape halting Problem : Turing machine halts if started with a blank tape.

證明的方法就是利用該 Problem 建構出 Halting Problem，但已知 Halting Problem is undecidable，因此該 Problem 也是 undecidable (反證法)。

<details>
    <summary>想知道更多？
</summary>
<ul>
  <li>Undecidable Problems for Recursively Enumerable Languages</li>
  <li>The Post Correspondence Problem</li>
  <li>Undecidable Problems for Context-Free Languages</li>
</ul>
</details>

## <a id="complexity"></a>Computational Complexity
我們只介紹 P Problem, NP Problem。
* P Problem : Includes all languages that are accepted by some *deterministic* Turing machine in polynomial time. 指的是有明確 polynomial time 的解法 (通常指的是暴力解)。
* NP Problem : Includes all languages that are accepted by some *nondeterministic* Turing machine in polynomial time. 提供一個解法，可以在 polynomial time 被驗證 (通常暴力解會是 exponential time)。

<details>
    <summary>想知道更多？
</summary>
<ul>
  <li>The SAT problem (NP)</li>
  <li>The Hamiltonian Path Problem (NP)</li>
  <li>The Clique Problem (NP)</li>
  <li>NP-compete Problem</li>
  <li>NP-hard Problem</li>
</ul>
</details>

## Resource
* An Introduction to Formal Language and Automata (Peter Linz)
* Introduction to Automata Theory, Languages, and Computation (Hopcroft, Motwani, Ullman)
* Introduction to the Theory of Computation (Michael Sipser)
* [正規語言Formal Language | Mr. Opengate
](https://mropengate.blogspot.com/2015/06/formal-language.html)
* [Theory of Computation & Automata Theory](https://www.youtube.com/playlist?list=PLBlnK6fEyqRgp46KUv4ZY69yXmpwKOIev)





