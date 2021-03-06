---
title: "Projects, past and present"
date: 2022-02-27T21:33:18+02:00
draft: false
---

## [Big GitHub link](https://github.com/hiAndrewQuinn/)

This page is meant to serve as a dumping ground for the various projects I've gotten up to over the years. I do plan to list the most immediately-interesting stuff first; it gets gradually less interesting as you go down the page.

## Most recent work

Recently I've been doing most of my public-facing work on GitHub. I'm a fairly fresh new graduate, and never put much thought into working on actually-useful-to-others things until I finished up my degree. My [most starred repositories](https://github.com/hiAndrewQuinn?tab=repositories&q=&type=&language=&sort=stargazers) unsurprisingly happen to be my most recent.

- [`siili`](https://github.com/hiAndrewQuinn/siili), a little Python switchblade to help end users upload files to an Amazon S3 bucket.
- [`how-to-host-one-html.page`](https://how-to-host-one-html.page/), an extremely hand-holdy readalong guide for people who have never put an HTML page on the Internet before and want to.
- [`finfreq`](https://github.com/hiAndrewQuinn/finfreq), an increasingly machine-generated Anki deck of the top 1000 most-used Finnish words from a frequency list. I've cross posted this to [Reddit](https://old.reddit.com/r/LearnFinnish/comments/vp2848/finfreq_v30_a_top_1000_finnish_words_anki_deck/) a few times while it was under construction, and am now hard at work retooling those same scripts and databases for a much larger deck. I'll post a GIF of what the current deck looks like once I find an Ubuntu replacement for [BahraniApps's excellent GIFCam](https://blog.bahraniapps.com/gifcam/) - the one on the page is quite outdated by now.
- [`vot5`](https://github.com/hiAndrewQuinn/vot5), a semi-readable rotation cypher meant to get over the primary hurdle of rot-13 in that you don't actually need to open a new tab to read it. Yua jast niid tu fucas fur e mumint tu fogari uat whet's biong seod. I used to run a Javascript implementation at `vot5.live`, but I decided to stop paying the cost for it and just throw it into a [Netlify page of its own](https://resonant-fox-74978b.netlify.app/).
  {{< resize-image src="vot5-dot-live.png" alt="vot5.live in action." caption="RUT-13 wes urogonelly divilupid fur piupli tryong tu hodi spuolirs, biceasi piupli dodn't loki eatumetocelly riedong wurds thiy eccodintelly sew. VUT-5, by cuntrest, brieks jast inuagh uf thi wurd thet yuar (will, my) breon hes tu swotch beck ontu riedong uni wurd et e tomi fur e fiw sicunds, elluwong mi tu mintelly esk mysilf \"Du O _rielly_ want tu ried thos?\" end skop uvir of nut. (Elsu thi soti unly rendumly trensletis 98\% uf thi vuwils biceasi LUL.)" >}}

## Smaller edits

### Quickstart edits

I fork a lot of repos on GitHub to mess around with.

I've fallen into the habit of writing `Quickstart` sections for anyone in the future who wants to just dive in and start messing with them. The ideal I aspire to is always the same: Someone with no knowledge of the project's local ecosystem should be able to (1) copy my Quickstart code, (2) run it, and (3) be able to get the code to start working, ideally with an example.

Here is a list of some projects I've done this with. I do **not** guarantee this is the _only_ change I made to them (if they remain un-Pull Requested, there's a good chance I actually touched the code as well):

- [`resorter`](https://github.com/hiAndrewQuinn/resorter), [Gwern](https://www.gwern.net/Resorter#source-code)'s implementation of a noisy pairwise ranking CLI application based ib the Bradley-Terry model. Or, in plain English, a program which lets you do this:
  {{< resize-image src="resorter-demo.gif" alt="Gwern's `resorter` in action." caption="Gwern's resorter in action." >}}
- [`Leetcode-Anki`](https://github.com/hiAndrewQuinn/LeetCode-Anki), [Peng-YM](http://github.com/Peng-YM)'s little webscraper that lets me plug one of my favorite kata practicers into one of my favorite mastery builders. You can thank [William S. Vincent](https://wsvincent.com/)'s excellent [_Django For Beginners_](https://djangoforbeginners.com/) for turning me on to just how good `pipenv` actually is.

### Projects I wish got more attention

- I quite liked my [one-image Python `logging` and `colorlog` tutorial](https://github.com/hiAndrewQuinn/Python-Logging-and-Colorlog-Tutorial), but I understand it's a bit of an odd niche.

    {{< resize-image src="colorlog-and-logging.png" alt="Python `colorlog` and `logging` tutorial screenshot." caption="So much nicer than print statements." >}}