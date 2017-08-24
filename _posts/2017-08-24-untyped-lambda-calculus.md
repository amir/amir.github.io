---
layout: post
title: Untyped Lambda Calculus
tags: [tapl, rust]
published: false
---
As I mentioned in an [earlier post]({% post_url 2017-08-16-tapl %}), I've been working through [Types and Programming Languages](https://www.cis.upenn.edu/~bcpierce/tapl/) in Rust. Chapters 5 to 7 of TAPL discuss untyped lambda calculus through an implementation of a simple expression-based language. Chapter 5 lays the foundations; chapter 6 focuses more on one of the concepts introduced in chapter 5; [de Bruijn index](https://en.wikipedia.org/wiki/De_Bruijn_index) and chapter 7 explores an ML implementation of the said language, but only how to evaluate the terms, and not how to parse them. The accompanying OCaml [implementation](https://www.cis.upenn.edu/~bcpierce/tapl/checkers/)'s parser is generated automatically from a Yacc grammar.

I've had good experiences writting parsers in Haskell using [parsec](https://hackage.haskell.org/package/parsec) and [attoparsec](https://hackage.haskell.org/package/attoparsec) before, so I started looking for parser-combinators in Rust. There seem to be three capable options:

* [combine](https://github.com/Marwes/combine)
* [chomp](https://github.com/m4rw3r/chomp)
* [nom](https://github.com/Geal/nom)

Combine even has the [combine-language](https://github.com/Marwes/combine-language) extension which is very similar to Parsec's [Text.Parsec.Token](http://hackage.haskell.org/package/parsec/docs/Text-Parsec-Token.html) which would've simplified the task of parsing lexical elements but I couldn't add it as a dependency to my project—due to compile errors which I'm sure has been because of my ignorance and lack of familiarity with Rust and Cargo. At the end I ended up choosing using layman's metrics, number of GitHub stars and nom won by a huge margin.
