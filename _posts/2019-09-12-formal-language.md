---
layout: post
comments: true
mathjax: true
title: "Formal Language (形式語言)"
categories:
  - Formal Language
tags:
  - theory
  - mathematics
---

這篇文章只會簡單的介紹 formal language，目的是用最快的速度擁有最粗淺的了解，如果對於這個領域還有興趣，可以再分項一一往下研究。
Turing Machine 在 1936 年由 Alan Turing 提出後，便奠定了現今電腦的基礎，整個 Formal Language 大約是在 1930-1940 年代發展成熟，而人類第一台通用計算機 [ENIAC](https://zh.wikipedia.org/wiki/%E9%9B%BB%E5%AD%90%E6%95%B8%E5%80%BC%E7%A9%8D%E5%88%86%E8%A8%88%E7%AE%97%E6%A9%9F) 則是 1946 的事情了。值得一提的是，Formal language 較好的翻譯應該是「[形式語言](https://zh.wikipedia.org/wiki/%E5%BD%A2%E5%BC%8F%E8%AF%AD%E8%A8%80)」，如果翻成「正規語言」的話，我會很好奇 regular language 會怎麼翻？

<!--more-->

## Overview
* [Definition : Languages, Grammars, Automata](#Definition)
* [Regular Languages and DFA](#Regular)
* Context-Free Languages and Pushdown Automata
* Recursively enumerable Languages and Turing Machine
* Context-Sensitive Languages and Linear Bounded Automata 
* The Chomsky Hierarchy
* Others
* Computational Complexity

## Why we study formal language theory?
>theory provides concepts and principles that help us understand the general nature of the discipline.

學習理論讓我們知道計算機科學的最核心的概念和原則，進而了解電腦的極限，而不用透過無意義的 trial-and-error 以及猜測來理解電腦，以更高的角度來看待計算機科學。

>the ideas we will discuss have some immediate and important applications.e.g. digital design, programming languages, and compilers.

就實作面來說，formal language 是 compiler 的理論基礎，因為 compiler 就是在處理語言和字串，本質上和 formal language 所探討的問題是一致的；programming languages 核心的概念也是把人類理解的語言，轉成機器可以執行的語言，不論高階語言還是低階語言，本質上都是處理語言和字串的轉換。

>the subject matter is intellectually stimulating and fun.

最後一個理由是，透過理解這些理論基礎和證明，會再次感受到前人研究的偉大，而我們也只是站在這些巨人的肩膀上，希望獲得新知識的過程能帶來無比的成就感以及樂趣。

## <a id="Definition"></a>Definition : Languages, Grammars, Automata
在開始討論 formal language 之前，我們必須對於要討論的對象做根本上的定義。
Languages 是一個數學上的字串集合；這些字串集合的 derivation rules 就稱為 Grammars；而設計一個自動機來決定給定的字串是否屬於該集合則稱為 Accepter (Automata 的一種)。

Languages 的例子：
$$ L_1=\{ a^nb^n : n \geq 0 \} $$

Automata 基本上分為兩種：
* Accepter : output response is limited to a simple “yes” or “no”.
* Transducer : producing strings of symbols as output.

Grammars 是用數學嚴謹的定義來描述 language：
* variables (V) : finite set.
* terminal symbols (T) : finite set.
* start variable (S) : special symbol.
* productions (P) : which used to derives the strings.

$$ 
G_1 = (\{A,S\},\{a,b\},S,P_1)\ with\ P_1\ consisting\ of\ the\ productions \\
S \to aAb|\lambda \\
A \to aAb|\lambda
$$

這個 Grammar 其實就是 Language 那個例子的 Grammar，所以 $$L(G_1) = L_1$$。

## <a id="Regular"></a>Regular Languages and DFA

## Resource
* An Introduction to Formal Language and Automata (Peter Linz)
* Introduction to Automata Theory, Languages, and Computation (Hopcroft, Motwani, Ullman)
* Introduction to the Theory of Computation (Michael Sipser)
* [正規語言Formal Language | Mr. Opengate
](https://mropengate.blogspot.com/2015/06/formal-language.html)
* [Theory of Computation & Automata Theory](https://www.youtube.com/playlist?list=PLBlnK6fEyqRgp46KUv4ZY69yXmpwKOIev)





