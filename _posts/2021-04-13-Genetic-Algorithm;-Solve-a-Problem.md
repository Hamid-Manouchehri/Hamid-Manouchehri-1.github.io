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

Suppose there are some sports competitions held in the university for students. Each student can participate in one or more competitions. If it is decided to hold _m_ matches simultaneously on the first day of the competition, we want to write a program using the genetic algorithm that receives a graph in which each vertex represents a match, and the edge between both vertices indicates the presence of at least one interested student. To participate in both competitions, let's specify these _m_ competitions.

### Solution

In the following, I will give you the general concept based on my source code on [GitHub](https://github.com/Hamid-Manouchehri/genetic_algorithm_case_study). Everything is clear, just follow the source code beside what I explain in here. :) <br>
1. The __adjacancy graph__ represents the model of the problem, _discrete binary representation_. The first row of `input.txt` file is _m_ and the rest of the lines define whether there is a vertex between _i_ and _j_ edges or not. The `input.txt` would be passed into `load_input` function to extract __adjacancy graph__ and _m_. <br>
2. After that, the `generation` function generates _chromosomes_ ramdomly, our goal is to find the most suitable chromosome (solution). <br>
3. Next we have to assign an _objective value_ via `obj_func` function. <br>
4. Then we deploy __roulette wheel__ for the selection step, chose chromosomes and do generation. It is executed by the `roulette_wheel` function.
5. After that, we need _crossover_ to produce one of the most important pillars of evolution, _diversity_. It is done by the `crossover` function.
6. Later, _mutation_ must be done. Mutation also leads to more diversity by taking the chromosomes away from the _local minima_ points for having broader range of chromosomes. <br>
7. Finally, the main routine, `solution` function, calculates the best chromosome as answer. <br>
In the following I will demonstrate how fast the algorithm finds the solution, it is done by 200 chromosomes, 25% crossover rate, 10% mutation rate, and 700 iteration. 

<p style="text-align:center;">
  <img width="1145" height="659" src="/img/genetic_algorithm/result.png" alt="result">
</p>

There may be some errors in the above parameters' values, but nothing important.


