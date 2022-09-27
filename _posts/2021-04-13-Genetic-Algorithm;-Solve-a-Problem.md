---
title:  "Genetic Algorithm; Solve a Problem"
mathjax: true
layout: post
categories: media
---

### Overview

[__Genetic Algorithm__](https://en.wikipedia.org/wiki/Genetic_algorithm) (GA) is a _metahuristic_ algorithm inspired by the process of __natural selection__, which is an __evolutionary algorithm__ (EA). It is mostly used for _optimization_ and _search_ problems. During the course of __Bio-Inspired Computing__, I could solve an optimization problem by GA. The algorithm consists of different steps based on what is happening in _Gens_ of biological creatures. Firstly we have to _model_ the problem, chose a genetic representation, then design a _fitness function_, after that, build a _population_, next choose a _selection_, _recombination_, and _mutation_ sequentially. Finally, devise a _termination condition_ and analysis procedure. According to the stochastic nature of GA, if we select the fitness function more suitable, it will lead to a better answer more quickly.

<p style="text-align:center;">
  <img width="487" height="540" src="/img/genetic_algorithm/GA.png" alt="GA diagram">
</p>

### Problem Definition

Suppose there are some sports competitions held in the university for students. Each student can participate in one or more competitions. If it is decided to hold __m__ matches simultaneously on the first day of the competition, we want to write a program using the genetic algorithm that receives a graph in which each vertex represents a match, and the edge between both vertices indicates the presence of at least one interested student. To participate in both competitions, let's specify these __m__ competitions.
