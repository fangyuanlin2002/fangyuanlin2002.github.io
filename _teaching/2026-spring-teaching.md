---
title: "UN4264/GR5264 Stochastic Processes and Applications"
collection: teaching
type: "Master course"
permalink: /teaching/2026-spring-teaching
venue: "Columbia University"
date: 2026-01-19
location: "New York, NY"
---

- Email: fl2744@columbia.edu
- Office Hours: 1-2pm Tuesday and 4-5pm Friday, School of Social Work (SSW) 1023.

## Quick Links
- [TeX Lecture Notes](https://www.overleaf.com/8582253538gzzmpybwrgsb#d87e5c)
- [Communication](#communication)
- [Student Check-In Form](#student-check-in-form)
- [Homework 2](#homework-2)
- [Homework 1](#homework-1)
- [FAQ](#faq)


## Communication
- **CourseWorks (Canvas)**: This is where you can find all the official materials, submissions, and annoucements.
- Please scroll down to see the comments I write about the homework/exams. The comments are based on the frequently asked questions during the office hours and my own insights.

## LaTeX Lecture Notes

I maintain a set of LaTeX lecture notes for this course, hosted on Overleaf:

**[Lecture Notes](https://www.overleaf.com/8582253538gzzmpybwrgsb#d87e5c)**

These notes are meant to supplement the lectures and Prof. Campbell's notes, and attempt to clarify technical details from my personal perspective. They will be updated throughout the semester. And everyone is welcome to contribute and edit :)


## Student Check-In Form

If you would like to share how the semester is going, what’s working or not working for you, or what kind of support might help, please use the form below. I do care and I do read the responses.

📝 **[Click here to fill out the Student Check-In & Support Form](https://forms.gle/QMjqctChV5wYqaBC7)**

Everything you share is confidential and meant to help me support you better. Whether you’re doing great, struggling a little, or just want to share feedback — I’m here to listen.


## Homework 2
- Due Thursday, March 5th midnight.
- Detailed solution will be posted afte the deadline.

### Problem 1 — Toy

<iframe
  src="{{ '/assets/animations/brownian_pyodide.html' | relative_url }}"
  width="100%"
  height="700"
  style="border: 1px solid #ddd; border-radius: 12px;">
</iframe>


### Problem 2 — Uncorrelated but not independent normals

- Try computing the cdf. Or mgf. Your choice.



### Problem 3 — Conditional expectation practice

- Do some algebra.


### Problem 4 - Are they martingales?
- Part 1: the laziest process. It just sits there. A process so boring that it can't help but be fair.
- Part 2: scale a martingale. 
- Part 3: Adding a drift? That sounds desirable for a lot of things. Like your wealth.
- Part 4: Compute the conditional expectation and see what happens.


### Problem 5 — Means and variances

- Part 1: just compute it :)
- Part 2: This is the geometric Brownian motion. Use Gaussian mgf.
- Part 3: Two independent Brownian motions multiplied together. They have nothing to say to each other.
- Part 4: Now we are multiplying a Brownian motion with itself at two different times. This is where the covariance structure actually matters. For the variance, try googling the fourth moment of normal distribution, or compute it yourself :)
- Part 5: A linear combination of independent normals. Shouldn't take too long :) Bonus observation: if a^2+b^2=1, then you get a Brownian motion.

### Problem 6 — Brownian scaling

- This is the Brownian motion is self-similar property. You can zoom in on time (speed it up by c) and zoom out on space (srink by sqrt(c)) and get exactly the same process back. Brownian motion is the fractal of stochastic processes - it looks the same at every scale. (try doing that with your stock portfolio).
- Verify the defining properties of Brownian motion: starting at zero, independent increments, Gaussian process, continuous sample paths.

### Problem 7 — Limiting Distribution of the Binomial Stock Price Model

- An analogous example was presented during lecture 10 Week 6 Monday.
- The central limit theorem does the heavy lifting.









## Homework 1
- Following are some emotional support lemmas. Full solution will be posted after the hw is due. As we probably all know, all these exercises are just trivial in the eye of AI models nowadays, but you will grow as a mathematician by playing around with problems.
- The first homework is entirely on the review of probability theory and does not involve stochastic processes.

### Problem 1 — Sigma-fields quick example

- This is problem is what mathematicians called *definition chasinggggg*. 

- Sigma-fields have exactly three personality traits:
1. They always want the whole universe.
2. They refuse to let go of complements.
3. A union of countably many members is also a member of the sigma-field.


### Problem 2 — Random variables gossip differently 

- Each random variable reveals at different resolutions of the same sample space. Revealing $X$ tells you exactly what $\omega$ happened, while revealing $C$ gives you no information.
- If you write out all the members of the sigma-fields, it might be a little tedious. We won't be doing something like this again later.


### Problem 3 — escaping of mass

- A sequence of functions can converge to zero pointwise everywhere and each term still integrates to one.

Yes, this is allowed.  
No, this is not a bug.

Also: before invoking Monotone Convergence, confirm that all conditions are satisfied.


### Problem 4 — Absolute continuity is one-way trust 

- Part 1: definition chasing.
- Part 2: state the definition of absolute continuity. Note that integrating an indicator of an event gives you the probability of that event.


### Problem 5 — Change of measure is identity theft 

- Part 1: Use a basic property of Gaussian distribution.
- Part 2: (i) what's the range of the exponential function? (ii) feel free to use an argument using moment generating function.
- Part 3: directly compute the right hand side of the formula and see what it becomes.


---






## FAQ
### “Should I be worried if this feels abstract?”
No. Stochastic processes are abstract at first.  
The intuition builds gradually. I like the following quote a lot. John von Neumann said we never understand anything in math. We just get used to it. 

### What does it mean for a function to be Borel-measurable?
This class does not assume a background in topology so that notion of Borel sigma-field (generated by open sets) would be confusing for a lot of us. This is just a mathematical jargon. Going forward, think of a measurable function (aka Borel-measurable) as a random variable. 




