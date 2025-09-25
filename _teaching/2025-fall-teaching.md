---
title: "STAT 3104 Applied Bayesian Analysis Fall 2025"
collection: teaching
type: "Undergraduate course"
permalink: /teaching/2025-fall-teaching
venue: "Columbia University"
date: 2025-09-02
location: "New York, NY"
---

- Email: fl2744@columbia.edu
- Office Hours: Mondays 1–2 PM, Fridays 3–4 PM, Watson Hall 601

## Quick Links
- [Communication](#communication)
- [Homework 2](#homework-2)
- [Homework 1](#homework-1)
  - [Problem 1](#problem-1)
  - [Problem 2](#problem-2)
- [FAQ and Troubleshooting Bugs](#faq)


## Communication
- **CourseWorks (Canvas)**: This is where you can find all the official materials, submissions, and annoucements.
- Please scroll down to see the comments I write about the homework/quiz/project. The comments are based on the frequently asked questions during the office hours and my own insights.

## Ways to Succeed in This Course
- **Keep on track** Consistency brings mastery. Don't skip lectures or homeworks.
- **Come to office hours** — They’re for you, whether you’re confused or just curious - ask questions early and all questions are welcome. I will do my very best to help.
- **You do not need to be a mathematician to succeed** — Don’t be afraid if the equations look heavy at first. The focus is on understanding ideas, running code, and interpreting results, not on doing pages of proofs. The intuition matters more than the algebraic details.


## Homework 2
Homework 2 is mostly about coding. 

Before we delve into model fitting, I would like to include a quick review of Bayesian linear regression, which is the topic of this week (Week 4 FYI).

### Quick Review of Bayesian Linear Regression
When we learn linear regression in the classical (frequentist) sense, we imagine a straight line trying to best fit our data points. "Best fit the data points" means that the squared errors of the straight line is minimized.
- This line can be exactly computed using a formula, but the formula and its derivation requires the knowledge of linear algebra and is beyond the scope of this course.
- In classical (frequentist) regression, once we compute the line, we treat the slope and intercept as fixed numbers.
- Bayesian regression takes a different viewpoint: Instead of saying “the slope is 2.1,” we say “given the data, we believe the slope is likely around 2.1, but it could also be 2.0 or 2.2 with some probability.” So in Bayesian regression, the slope and intercept aren’t fixed. They’re random variables with distributions that represent our uncertainty about them.
- In lecture, we learned that Ptolemy’s geocentric model wasn’t mechanistically true, but it was descriptively accurate: it gave good predictions. Regression works the same way: it doesn’t explain the “true mechanism” of the world, but it’s a flexible way to approximate relationships in data.

### Problem 1:
The first problem is a guided application of Bayesian linear regression to global temperature data.

- Download the dataset from the link in the homework. The first column is the year, the second is the change in global temperature
-Part a: Fit a Bayesian linear regression. The question asks you to use priors with large standard deviation, i.e. weakly informative (50 is a reasonable choice for the standard deviation in case you are struggling to choose one).
- Part b: State the posterior mean for the slope. Is it positive or negative? On average, there has been a "slope" degree Celsius increase/decrease per year.
- Part c: Provide plot of the densities for the three parameters.
- Part b: Use Monte Carlo simulation. Calculate the porportion of samples for which the posterior mean of the slope obtained is positive. Intuitively, this probablity should be equal or close to 1 just by thinking of global warming.
- Part e: Change the variance of the prior for b to something very small (like 0.001). Does any of our conclusions change?
- Part f: What statistical arguments can we make? Here are two points you can make: Is the posterior mean of the slope positive or negative? Does the conclusion hold regardless of the whether we use an informative or diffuse prior?


## Homework 1

### Problem 1:
- The demo the professor presented at the end of the lecture on Sep. 9th is relevant.
- Generative AI is great at producing plotting code. Make sure you really understand what the code is doing, and how the grid approximation reflects Bayesian updating.

### Problem 2:
- Pandas are cute 🐼
- Be clear what events we are considering.
- For part a, recall the law of total probability.
- For part b, Bayes' rule is your tool. Observing a twin should strengthen your belief that the species is the one that gives birth to twins with more probabiility, right? :)
- For part c, I would use Bayes' rule.
- For part d, follow the hint. As new observations come in, the previous posterior becomes your current prior. 


## FAQ and Trouble Shooting Bugs {#faq}

### R Session aborted when using R-Studio
It's experimentally shown that if your macOS version is something like is 12.5, you should still download R-Studio using the [macOS 13+ (macOS 13 and higher)] option on the official site.
