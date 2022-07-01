---
title: "Github’s `gh` and the art of Unix programming"
date: 2022-07-01T12:31:54+03:00
draft: false
tags: [computer-science,engineering,unix,git,esr]
---


Take a look at the recent-ish Github CLI interface, `gh`:

```bash
andrew@andrew-XPS-13-9310:~/Documents/Github/_Django-for-Beginners$ gh repo create
? What would you like to do? Create a new repository on GitHub from scratch
? Repository name d4b_blog
? Description ch4 django for beginners
? Visibility Private
? Would you like to add a .gitignore? Yes
? Choose a .gitignore template Python
? Would you like to add a license? Yes
? Choose a license MIT License
? This will create "d4b_blog" as a private repository on GitHub. Continue? Yes
✓ Created repository hiAndrewQuinn/d4b_blog on GitHub
? Clone the new repository locally? Yes
Cloning into 'd4b_blog'...
fatal: unable to access 'https://github.com/hiAndrewQuinn/d4b_blog.git/': Could not resolve host: github.com
exit status 128
andrew@andrew-XPS-13-9310:~/Documents/Github/_Django-for-Beginners$ 
```

A long list of interactive yes-or-no questions, guiding you through the creation of a GitHub repo. It's been a surprisingly long while since I've seen a _good_ command line program that works as a series of yes/no questions like this. Why?

Like always, we can get some insight into why they don't appear that often _on Unix_ by looking at Eric S. Raymond's [basics of the Unix philosophy](http://www.catb.org/esr/writings/taoup/html/ch01s06.html), specifically where it breaks things. The most obvious place to look is an interactive command-line interface breaks is the [Rule of Silence](http://www.catb.org/esr/writings/taoup/html/ch01s06.html#id2878450).

> One of Unix's oldest and most persistent design rules is that when a program has nothing interesting or surprising to say, it should _shut up_. Well-behaved Unix programs do their jobs unobtrusively, with a minimum of fuss and bother. Silence is golden.
> 
> This “silence is golden” rule evolved originally because Unix predates video displays. On the slow printing terminals of 1969, each line of unnecessary output was a serious drain on the user's time. That constraint is gone, but excellent reasons for terseness remain.
> 
> I think that the terseness of Unix programs is a central feature of the style. When your program's output becomes another's input, it should be easy to pick out the needed bits. And for people it is a human-factors necessity — important information should not be mixed in with verbosity about internal program behavior. If all displayed information is important, important information is easy to find.
> 
> -- Ken Arnold
> 
> Well-designed programs treat the user's attention and concentration as a precious and limited resource, only to be claimed when necessary.
> 
> (We'll discuss the Rule of Silence and the reasons for it in more detail at the end of [Chapter 11](http://www.catb.org/esr/writings/taoup/html/interfacechapter.html "Chapter 11. Interfaces").)

Clearly `gh` nails it on the "type as few characters as humanly possible" into the keyboard. They're even right next to each other, and are supposed to be typed by alternating hands (on QWERTY).

But wait a minute. "\[N\]othing interesting or surprising to say"? The _whole point_ of `gh` is to give a streamlined CLI interface to GitHub specifically. The loud interactive output _is_ the interesting thing! Of course, the underlying software has _another_ interface that actually does follow the Rule of Silence when things are going smoothly - `git`, itself.

Much like Piotr Wozniak’s [20 rules of knowledge formulation](https://supermemo.guru/wiki/20_rules_of_knowledge_formulation) for first-generation[^1] [spaced-repetition systems](https://www.gwern.net/Spaced-repetition), I like to read ESR’s rules as roughly descending in terms of priority. The first 20% / 3 rules provides 80% of the value, and it’s best not to get hung up on the other 14 just because they appear to be more concretely suitable to the situation. What were [those first 3 rules again](http://www.catb.org/esr/writings/taoup/html/ch01s06.html)?

> -   Rule of Modularity: Write simple parts connected by clean interfaces.
>     
> -   Rule of Clarity: Clarity is better than cleverness.
>     
> -   Rule of Composition: Design programs to be connected to other programs.
>     
> -   Rule of Separation: Separate policy from mechanism; separate interfaces from engines.

Okay, that’s actually 4 rules. But I think the [Rule of Separation](http://www.catb.org/esr/writings/taoup/html/ch01s06.html#id2877777) is the obvious real fit here. If we consider `gh` not as a standalone program, but as an _interface_ to `git`, suddenly it makes perfect sense why it’s allowed to be loud and interactive. Being loud and interactive [clarifies](https://www.wikiwand.com/en/Expert_system) what’s actually going on, the same way a good old-fashioned [expert system](https://www.wikiwand.com/en/Expert_system) does.

And of course, if we actually _need_ to [compose](http://www.catb.org/esr/writings/taoup/html/ch01s06.html#id2877684) programs later on in a pipe-like fashion, `gh` isn’t going to be our go-to choice — we’re going to invest the time into figuring out how to properly shell out to `git`, because it will be much easier to work with. Spend 20 minutes messing around with getting your terminal to pretend to give interactive input to another program with its own shell and you’ll see just how irritating it is.

I remember writing a bunch of scripts in college to automate the build process of my Verilog designs for [COMP_ENG 303: Advanced Digital Design](https://www.mccormick.northwestern.edu/electrical-computer/academics/courses/descriptions/303.html) I was doing that required a lot of interactivity, and it was absolute _torture_. A brittle mess I wouldn’t foist on anyone except myself, since I was using it literally every week as it was for tiny little homework assignments where the actual Verilog coding took maybe 10% of my time up. It was so bad that part of the reason I went out of my way to finally learn Haskell properly last winter was simply so that if I ever had to work on a hardware design again, I could at least [work with modern tooling](https://clash-lang.org/).

There’s a point underneath the point here, for anyone else obsessed with committing long lists of rules to the back of their memory, on how to most productively use these lists. When I was a teenager, I combed through _The 48 Laws of Power_. After I got fluent with using the laws as mental shorthand for the thankfully rare times I had to be careful with the people I dealt with, it dawned on me that a lot of situations I faced in real life had many different laws that _might_ be the best way forward — ultimately I had to tally up the pros and cons from the surrounding context in order to figure out what was most likely to be the actual best move.

This might make the book sound like it was useless, but in reality it made it far more helpful than anything else I read on the subject: By presenting me with a handful of distinct possibilities, *but not infinitely many*, and then letting me figure out for myself when the situation is better suited for one rule over the other, I was able to engage my own critical thinking while still having some useful signposts as to where to go. 

So too it is with ESR’s (in)famous rules list. Take a moment to double-check the context a little bit before using whatever rule appears most salient to your own mind. “Separate interfaces from engines” might not spring to mind as quickly as “If a program has nothing interesting to say, it should say nothing” when looking at a chatterbox like `gh`, and it might be your ammunition to reflexively discount it. But that’s just because one rule _actually talks explicitly_ about shutting up.


[^1]: “First-gen” here refers to programs where you input the information you want to retain yourself, such as SuperMemo, Anki, Mnemosyne, or that one `org-mode` extension. You know, the ones people usually mean when they say “SRS”. But [spaced repetition systems are just a subspecies of recommender systems](https://uwspace.uwaterloo.ca/bitstream/handle/10012/13715/2017-Recommender%20Systems%20for%20Personalized%20Gamification.pdf?sequence=3), and their influence looms far and wide across the Internet now. [Duolingo](https://research.duolingo.com/) and [Khan Academy](https://www.khanacademy.org/) both use spaced-repetition principles in their designs, specialized to their specific topics, and so I’ve taken to calling them “second-generation” spaced repetition systems. The massive, near-professionally made decks made available for purposes like [beating the U.S. medical schooling system](https://www.reddit.com/r/medicalschoolanki/) or the [Indian board exams at the end of 12th grade](https://github.com/Raagaception/raagaception-12STD-CBSE-deck)  might be called “1.5 gen”, a bridge between worlds. (My [Finnish-learning decks](https://github.com/hiAndrewQuinn/finfreq) are more like v1.1.)