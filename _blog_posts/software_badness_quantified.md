---
layout: blog_post
title: Software badness quantified
permalink: /blog/software-badness-quantified/
content_type: BlogPosting
image: /img/blog/software_badness_quantified/programming-code.jpg
image_description: An abstract image of lines of programming code on a computer screen.
image_display: true
order: 200
tags: [digital services delivery, robert read]
excerpt: Until a more robust model for measuring technical debt is developed, we suggest using a simple formula for measuring the "badness" of a codebase in order to make improvement decisions.
authors:
  - Robert Read
date_published: 2017-04-29
date: 2017-04-29
---

<blockquote cite="http://quoteinvestigator.com/2012/04/28/shorter-letter/">If I had more time, I would have written a shorter letter. &mdash; <a href="http://quoteinvestigator.com/2012/04/28/shorter-letter/" target="&#95;blank">attribution unclear</a></blockquote>

<blockquote cite="http://www.paulgraham.com/power.html">Succinctness is power. &mdash; <a href="http://www.paulgraham.com/power.html" target="&#95;blank">Paul Graham</a></blockquote>

> Great literature is simply language charged with meaning to the utmost possible degree. &mdash; Ezra Pound

Programming, a form of literature, is greatest when it does the most with the least.

The job of a programmer is to produce order out of chaos, and the more compactly that order can be expressed the better.

Although we can all think of exceptions which prove the rule, shorter code is better code in general.

But how is the software architect or executive to make use of this? It is all very well for programmers to talk about regular expressions, lambda-lifting, and higher-order programming, and I wish more did. But many of us are stuck in the dreary dull world of enterprise software where oceans of fluffy code suffocate the user, like a child falling into a vat of cotton candy. Working with enterprise software sometimes feels like beating a cloud.

What is really needed is a model of technical debt that would allow software engineers to speak with a precision and certitude similar to accountants and structural engineers. A structural engineer can, with enough study, tell you what load a bridge should bear. An accountant, with enough study, can tell you with some certainty the soundness of a firm by examining the books. Software engineers cannot at present tell you the soundness of a codebase.

We can of course judge a codebase by two active criteria: if people use it, it is valuable. If it is testable, it is somewhat sound, to the extent that our tests measure fitness. But we cannot examine a codebase and determine what the maintenance costs will be.

Codebases tend to have <a href="https://18f.gsa.gov/2015/09/04/what-is-technical-debt/" target="&#95;blank">technical debt</a>. That is, they have problems which are not apparent at first use or inspection which prevent the evolution of the codebase efficiently and increase the maintenance costs. I will take my hat off to anyone who can produce a good model of technical debt that is as useful as double-entry bookkeeping.

But in the meantime, I suggest this simple formula for measuring the "badness" of the a codebase: **B = L<sup>2.5</sup>**.

Where **B** is the "badness" of the code, and **L** is the number of lines of code in the system.

Obviously, this is a bit of joke, but there is a grain of truth in any good joke.  We do not have a crisp definition of "badness." And two systems can have equal badness with different numbers of lines of code, so this equation cannot be, strictly speaking, true. A physicist will point out that a dimensional analysis of this equation produces nothing meaningful at all, whereas E = mc<sup>2</sup> actually produces units of kg.m/s<sup>2</sup> (Joules) on both sides. Nonetheless, if forced to give a rule for code badness in only six symbols, I will stand behind this one as the best possible.

Q: When can we possibly compare the "badness" of a system to something in order to make a decision?

A: When we compare it the badness of a modification of the same system.

In other words, badness makes sense relative to improvements in the same system. Using this formula, we can predict that the that a 10% decrease in the number of lines of code leads to a 23% decrease in bugs and operational cost, and 20% decrease leads to a 43% decrease in bugs and operational costs. Cutting the code length in half reduces the cost to 17% of the original cost. Cutting the code length to 10% of the original reduces the cost to 1.7% of the original.

This may seem fantastic. Surely the exponent is too high &mdash; maybe **B** is just the square of the number of lines of code?

But let us consider the total cost of ownership. Suppose there is a 1-million-lines-of-code project and you could wave a magic wand and make it a 100K-line system with approximately the same quality. This is approximately a change from a 10-person maintenance system to a 1-person maintenance team. Significant, but not 1.7%. But let us now consider the cost of rewriting the system every 10 years to keep up with changes in technology. Rewriting a 100K system is far more manageable. That is something that a programmer could probably personally do in one year, as opposed to a team. A team is much harder to manage than a single person &mdash; there is significant communication overhead on a team. It is much more expensive to hire a team.

Additionally, the small system could be expected to have 10% of the bugs of the original system. If each bug costs you something in user satisfaction, that surely must be counted. Even more importantly, the cost of fixing each one of these bugs will be less, and the time to turn them around and the danger of introducing a new bug will be much less. The cost of performing enhancements will be considerably less. Taking these things into account, we are now getting much closer to 1.7% the cost of the mega-line project.

Consider also that some systems become so complex that attempts to rewrite them fail completely. This is hard to work into a cost estimate, but surely it is a point in favor of a nonlinear decrease in costs as well. In government work, this is perhaps easier to understand. How much would the Air Force pay for more reliable and secure software for its systems? At some point, bugs and the inability to make enhancements starts to become a strategic problem that cannot be expressed in a spreadsheet.

Believe it or not, I am a mathematician and computer scientist. I like proofs. I love proofs. We are not operating in the realm of proofs.

We all know the exponent is not 2.5; I pulled that out of my hat to match my experience rewriting and maintaining legacy systems.

But I will defend the proposition that the exponent is closer to 2.5 than 2.0, and I hope I have convinced you that 1.5 is out of the question.