---
title: "Why is AWS documentation bad so often?"
date: 2022-07-23T13:05:20+03:00
draft: false
---

Last week I used [Google Takeout](https://takeout.google.com/) to grab some tarballs of my data (mostly photos I never look at), so that I can finally close down my old email account for good. It was around 80 GB in total. I didn’t want to _just_ keep that tarball on my local machine, of course; a tornado could lash its windy tail down right at the centroid of my laptop and thresh it into a thousand pieces.

So I decided, against some ancient trepidation whispering _Don’t do it! Don’t summon the Bezos!_, to try out AWS for my use case again. My plan was simple:

1. Find out how to put things in Amazon S3.
2. Put my tarballs there in the cheapest archive storage they have.
3. Log off and not think about it for another 5 years.

80 GB would cost around [$22 / year](https://aws.amazon.com/s3/pricing/) to store in S3 Standard — wait, what? That’s _more_ expensive than Google Photos! What gives? Ah, but S3 Glacier Deep Archive would cost less than $1 / year for 80 GB. Done and done.

When it came to actually finding what I was looking for, though:

{{< resize-image src="amazon-search-woes.gif" alt="A montage of DuckDuckGo searches for 's3 upload' and only getting Amazon official documentation." caption="AWS documentation kudzu growing on the walls of my innocent search wall." >}}

Apparently AWS’s docs team is really, really good at SEO.

Maybe _too_ good at it. I realized later that what I probably should have done was go directly to Stack Overflow, or Reddit, or Twitter, and asked people there who have actually been working with the technology directly.

The last time I touched AWS, it was years ago, for a student project, thankfully extracurricular, and my teammate buried his head in his hands and yelled “_THIS IS SO LOW LEVEL_” in frustration. We probably read through a dozen docs before we got to a single line of working code. That was in college; we were attempting to get a simple messaging system going to an embedded device.

That project didn’t pan out to anything. I felt then, as now, like an idiot for not understanding whatever it was about AWS’s deal was. It felt like _surely_, there had to have been an easier way.

I ended up writing myself [a tool](https://github.com/hiAndrewQuinn/siili) to make S3 uploading easier on myself, and posting it to Reddit, where I got the very helpful answer _Why didn’t you just use `aws s3 cp`_? I slunk out of the metaphorical room!

But perhaps I shouldn’t have — the easier it is for new users to start using your product, the more new users you’ll hook into the ecosystem. And the more revenue this generates a bit lower on the sales funnel. I get that AWS might not have that as a concern for now, being as large as they are, but Azure (what my previous job was on) and GCP are both making serious headway, and part of the reason is their much better kept documentation gardens.