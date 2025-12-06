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
- Office Hours: Mondays 1–2 PM, Uris 321 and Fridays 3–4 PM, Uris 319.

## Quick Links
- [Communication](#communication)
- [Student Check-In Form](#student-check-in-form)
- [Final Project](#Final-Project)
- [Homework 5](#homework-5)
  - [Problem 1](#problem-1)
  - [Problem 2](#problem-2)
- [Homework 4](#homework-4)
  - [Problem 1](#problem-1)
  - [Problem 2](#problem-2)
- [Homework 3](#homework-3)
  - [Problem 1](#problem-1)
  - [Problem 2](#problem-2)
  - [Problem 3](#problem-3)
- [Homework 2](#homework-2)
- [Homework 1](#homework-1)
  - [Problem 1](#problem-1)
  - [Problem 2](#problem-2)
- [FAQ and Troubleshooting Bugs](#faq)


## Communication
- **CourseWorks (Canvas)**: This is where you can find all the official materials, submissions, and annoucements.
- Please scroll down to see the comments I write about the homework/quiz/project. The comments are based on the frequently asked questions during the office hours and my own insights.

## Student Check-In Form

If you would like to share how the semester is going, what’s working or not working for you, or what kind of support might help, please use the form below. I do care and I do read the responses.

📝 **[Click here to fill out the Student Check-In & Support Form](https://forms.gle/NabKk9YjunpETDd4A)**

Everything you share is confidential and meant to help me support you better. Whether you’re doing great, struggling a little, or just want to share feedback — I’m here to listen.

- Feedback 1: "having a document summary of what was covered would be awesome."
- My response to Feedback 1: Thank you very much for the suggestion. I love the idea—but I don’t have the bandwidth to write them myself, but I’m launching a crowdsourced project on Overleaf and inviting anyone who’s interested to contribute concise summaries of key concepts, techniques, and example code. Of course, I will be there to maintain it!
It’s a great way to reinforce your understanding of Bayesian ideas while learning some LaTeX coding—a skill that’s incredibly useful in research and technical writing. It’s also a fun way to build rapport with classmates and be part of something meaningful that future students can benefit from. Contributors will be noted if they wish. The link is below:

[Click here to join the project!](https://www.overleaf.com/2354589638gqpgxqftkxxx#f794b3) 
## Ways to Succeed in This Course
- **Keep on track** Consistency brings mastery. Don't skip lectures or homeworks.
- **Come to office hours** — They’re for you, whether you’re confused or just curious - ask questions early and all questions are welcome. I will do my very best to help.
- **You do not need to be a mathematician to succeed** — Don’t be afraid if the equations look heavy at first. The focus is on understanding ideas, running code, and interpreting results, not on doing pages of proofs. The intuition matters more than the algebraic details.


## Final Project
Please take this opportunity to investigate a question that genuinely interests you!


## Homework 5

Homework 5 notes will hopefully be here soon. I accidentally spilled water on my laptop and it didn’t survive — my prior that “a water cup is dangerous” has now been updated from 0.1 to 1.0 (just kidding… 1.0 is an exaggeration). 

- This is Week 14! The last week of class.
- You are encouraged to fill out the evaluation for this course! It's been an honor to learn alongside you.

### Problem 1: 
- Part a: This part demonstrates how the choice of prior can matter. Define your model as 
<pre><code>
## Model 1
ulam(
  alist(
    y ~ bernoulli(p),
    p <- theta[s],
    theta[s] ~ dbeta(FILL IN THIS)
  ),
  data = touch_data,
  chains = 4,
  iter = 2000,
  log_lik = TRUE
)
</code></pre> 
To get the contrast, run 
<pre><code>
post <- extract.samples(YOUR MODEL)
contrast <- post$theta[, 28] - post$theta[, 1]
</code></pre> 
You should get a number that is close to 0.3XXX.

- Part b: Repeat part a with model 2. 
- Part c: Smaller WAIC means better fit.
- Part d: I was disappointed to find there's no magic in this world.


### Problem 2:
- Part a: Run the provided the code. The HPDI is something like 0.75-0.8.
- Part b and c: Data imputation doesn't change the result of our analysis very much, though the new estimate of the slope might be slightly higher. Also make a plot to see whether the imputed data would drive the slope higher, lower, or no effect.


## Homework 4
This is Week 10. 
### Some tips
- When modeling count data, such as the number of salamanders in a plot, we typically assume the response variable follows a Poisson distribution. The lecture slides of Week 9 provide a detailed introduction to the Poisson regression.
- We were working with linear regression the entire time. This homework shifts gear to Poisson regression and logistic regression. They are harder than linear regression models in the sense that linear regression model is easier to interpret and has an explicit formula (you don't need to be able compute the formula of linear regression model because it would require the knowledge of matrix algebra). Worry not, the course is not getting more difficult though. For the purpose of this course, you should, first, intuitively understand the new regression techniques (review the lecture slides if you don't have an intuitive understanding), and second, write R code to analyze data using these new regression models. I have written some comments below that are intended to guide you through this assignment. I intentionally provided a lot of example code (and you may find this assignment very straightforward with my example code) because I believe that memorizing the grammar of R is not as important as understanding the workflow of data analysis.

### Problem 1:

- Part a: Check: You should see lower accracy when the value of the predictor is high. The following code constructs the model.
<pre><code>
m1a <- ulam(
  alist(
    count ~ dpois(lambda),
    log(lambda) <- a + b * cover, # This is the how Poisson regression is defined
    a ~ DEFINE YOUR PRIOR
    b ~ DEFINE YOUR PRIOR
  ),
  data = mod_data,
  chains = (I would put a four here),
  cores = (I would put a four here),
  log_lik = TRUE
)
</code></pre>

- Part b: Hint: if the coefficient of the new term is very big, then the forest age might be an important predictor. If the coefficient is very small, then we consider it as an unimportant predictor.

Your model should be 
<pre><code>
ulam(
  alist(
    count ~ same as before
    log(lambda) <- a + b * cover + b2 * age,
    a ~ Define your prior
    c(b, b2) ~ Define your prior
  ),
  data = mod_data,
  chains = 4,
  cores = 4,
  log_lik = TRUE
)
</code></pre>

### Problem 2:
- Part a: First load your data. Then construct the logistic regression model.
<pre><code>
b_data <- read.csv(file.choose())
b_data$r_cat <- as.factor(b_data$rank)

glm(admit ~ FILL_IN_PREDICTOR_1 + FILL_IN_PREDICTOR_2 + FILL_IN_PREDICTOR_3, data = b_data, family = binomial)

summary(m2a)
</code></pre>
Think about why we set family to be binomial. (It's a quick question, not a trick question.)

You can use the following fact to check your solution: the intercept of the model should be about -3.99 

- Part b: Use quap:
<pre><code>
m2b <- quap(
  alist(
    admit ~ Your prior,
    logit(p) <- a[r_cat] + b_gre * gre + b_gpa * gpa,
    a[r_cat] ~ Your prior,
    b_gre ~ Your prior,
    b_gpa ~ Your prior
  ),
  data = b_data,
  start = list(a = rep(0, 4), b_gre = 0, b_gpa = 0)
)

precis(m2b, depth = 2)
</code></pre>
- Part c: 

<pre><code>
m2c <- ulam(
  alist(
    same as part b
  ),
  data = b_data, chains= FILL_IN_YOURSELF , iter= FILL_IN_THIS_YOURSELF
)

precis(m2c, depth = 2)

traceplot(m2c)

</code></pre>
- Part d: discuss the intercepts and the coefficients of the models.

## Homework 3
Time flies. This is Week 8.
### Some tips
- ANOVA stands for Analysis of Variance. Despite the name, it’s really about comparing group means — the “variance” part refers to how we measure differences between those means. Here's an example. Suppose we have 3 groups of students. Group A is the students who study in the morning. Group B is the students who study at night. Group C is the students who don’t study at all. Your measure their exam scores and ask: Do these groups have different true average scores, or could the differences be just random noise? ANOVA separates total variability in the data into two parts: Total variability = Between-group variability + Within-group variability. The idea is that if between-group variation is large compared to within-group variation,
then it’s evidence that the group means are really different. In the Bayesian framework, instead of testing a null hypothesis, we compute the posterior distributions of the group means and their differences and we can say things like: “There’s a 95% posterior probability that Group A’s mean is higher than Group B’s mean.”

- It's useful to know that the posterior distribution is often difficult to compute analytically. This is why we introduced the method of Monte Carlo - so we can sample the posterior using Monte Carlo.


### Problem 1:

- Part a: Even if you can see quite easily how many groups there are by clicking on the csv file on CourseWorks (you would be groups like 'A', 'B', etc), please still write code the find out the answer. The group_by() and nrows() functions can be helpful. The answer to this quesiton is easily generated by chatbot; just make sure to understand what's going on. 
- Part b: Here is a sanity check. For group A, the sample mean should be 90.000 and the posterior mean should be 90.575. Here's some more detail. First, do 
<code>
anovadata$GroupIndex <- as.numeric(as.factor(anovadata$Group))
</code>
Then your model should be 
<pre><code>
ulam(
  alist(
    Y ~ dnorm(mu, sigma),
    mu <- a[GroupIndex],
    a[GroupIndex] ~ dnorm(FILL_IN_THE_PRIOR_MEAN, FILL_IN_THE_PRIOR_VAR),
    sigma ~ dunif(FILL_IN_THE_PRIOR_MEAN, FILL_IN_THE_PRIOR_VAR)
  ),
  data = anovadata, chains = 4, iter = 2000, cores = 4
)
</code></pre>
- Part c: Use the <code>HPDI()</code> function.
- Part d: Repetition of parts b and c.

### Problem 2:
- Part a: We are given 
<pre><code>
mp <- ulam(
  alist(
    a ~ dnorm(0, 1),
    b ~ dcauchy(0, 1)
  ),
  data = list(y = 1), iter = 10000, warmup = 200, chains = 2
)
</code></pre>
Then you can simply do <code>post <- extract.samples(mp)</code> and then run <code>summary()</code> and <code>hist()</code> on <code>post$a</code> and <code>post$b</code>.
- Run <code>traceplot(mp)</code>.

### Problem 3:
- Describe the structure of the two histograms. Do we have symmetry? Skewness?


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
