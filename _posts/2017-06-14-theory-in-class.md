---
layout: post
title: In Defense of Theory in Class
tags:
- CS
- College
---

# Introduction
A common complaint I see amongst undergraduate computer science students is that their program
contains too much theory, and not enough practical experience. Usually, this refrain takes the
form:

> Why am I learning about (*program verification/induction/algorithm analysis/etc.*) when it
> would be much more useful to be learning about (*node.js/angular.js/ruby on rails/etc.*)?

I've noticed this often becomes a kind of holy war for those who espouse this 
position <sup id="a1">[1](#f1)</sup>. Holy wars nowithstanding, I think that this complaint is often
caused by confusion over both a.) the purpose of a university and b.) the practical value of generic
skills versus specific skills. In the interest of defending both my profession, and my Alma Mater and
professors (many of whom I am rather fond) let's see if I cannot dispel some of that 
confusion <sup id="a2">[2](#f2)</sup>.

# The Purpose of a University
Most people who attend a computer science program  plan to complete a four year degree, then take
a job as a programmer at either a defense contractor or Sillicon Valley startup – depending
on which coast they went to school. A minority <sup id="a3">[3](#f3)</sup> will wind up spending 
an additional couple of years at school, getting an advanced degree, and becoming researchers.
For the majority of undergraduate students, university is a four(-ish) year training program before
they are released into the workforce.

It is then, perhaps, understandable that a number of these students come to view the purpose of the 
university as providing that four(-ish) year training camp. If that is why *they* are there, is it not
why the school is there? Of course this self-centered view, though reasonable *prima facie*,
is quite wrong. Most universities are research institutions: their purpose is to train researchers. It is
merely a happy byproduct of creating researchers that a university trains professionals for industry.
The remaining universities are for-profit institutions: their purpose is to fleece you out of your 
money.

We can now see the disconnect between the students and the university. The school is focused on the 
minority, while the majority thinks the school is focused on them. So while the school teaches the
kind of things that it would want it's researchers to know: grammars, program verification, induction,
recursion, automata, etc., there is a cadre of students who really wanted to go to a programming 
bootcamp and learn about a language and framework they can use to make money who are going to 
be disappointed. The percieved value of the theoretical education to the student is less than the
percieved value of a more concrete education. This is understandable, but also wrong as I will
address next.

# The Value of a Theory Heavy Education
It would appear reasonable that it learning the latest technology would be more valuable than
learning an old technology. On deeper inspection however, "the latest technology" is a treadmill from
which a student is unlikely to ever escape. During the time I was in college, multiple technologies
came and went. Ruby on Rails began its meteoric rise early on, and by the time I had graduated, it
was starting to be considered a staid technology for the old fogies. Towards the middle/end of my 
time in school, Node.js was the hot newness, and already its star seems to be beginning to fade.
MongoDB was going to save us all, until it wasn't. MapReduce was huge, until people realized that
tiny ecommerce sites might not necessarily require that capacity.

My point is not to belittle these technologies. After all, every tool has a place on the 
shelf <sup id="a4">[4](#f4)</sup>. However, the latest shiniest tool changes all the time. If your 
school spends four years teaching you to write `jsp` pages, you're going to be unhappy when you're
applying for jobs and get told that nobody needs *or* wants a `jsp` programer.

The theory taught in computer science courses on the other hand doesn't change. It's math, and for
our purposes, math doesn't change. If you can judge the runtime of an algorithm in `Ruby` you can do
it in `Javascript`. Do you understand how a state machine works, finite or otherwise? What do you
think a computer **is**? Theory provides a much sounder foundation for a successful career. If you
know *why* your're doing something, *how* you do it becomes much simpler.

# Conclusion
If you are a programmer reading this, and you felt you didn't get a current enough education
in school, I hope to have persuaded you otherwise. Your theory heavy classes were much more useful
to you than you may have thought. It's those underlying concepts that are eternal and that you use
every day. This isn't to say that you shouldn't try to stay current, but college wasn't the place to get
there.

If you are not a programmer reading this, why did you read this far? Since you did, hopefully you 
learned something. If nothing else, you now know some boring "inside programming baseball" that
you had no desire to know anyway.

***
<a name="f1">1</a>:  Beside the counterarguments laid out in this piece, this seems to me
to be a counterproductive tack to take. Why convince yourself that your degree is less useful than
it could or should be? [↩](#a1)

<a name="f2">2</a>: Spoiler: I can't. [↩](#a2)

<a name="f3">3</a>: Probably. Just spitballing here.[↩](#a3)

<a name="f4">4</a>: Except for PHP.[↩](#a4)