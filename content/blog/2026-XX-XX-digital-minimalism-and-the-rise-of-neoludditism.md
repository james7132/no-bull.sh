+++
title = "Digital Minimalism: The Rise of Neoludditism"
path = "blog/2026/01/23/digital-minimalism-the-rise-of-neo-ludditism"
date = "2026-01-23"
draft = true

[taxonomies]
tags = ["Digital Minimalism", "AI"]
+++

About 10 years ago, I lambasted a few folks over their insistence on using
Windows XP in 201X. They had crawled out of 4chan's /g/ board raving like
lunatics, hurling insults at everyone using anything newer than 2006. At first I
thought they were trolling. They weren't. They were dead serious. They had
rejected the idea of connecting an operating system with multiple unpatched
zero-click RCE vulnerabilties to the open internet wasn't great for
one's infosec. They said putting it in their home network's DMZ was sufficient
to protect them (it's not). To them, offering their machine up to join every
botnet on the planet was better than running whatever new hotness Microsoft
was peddling at the time. They were clearly missing a few marbles, so I just
wrote them off as Luddites and ceased to entertain them any further.

Fast-foward to 2026 and now that sentiment is *everywhere*. ZIRP has ended years
ago, and we're now feeling every pang of the hangover.  Each new release of
software is packed with anti-features. Applications not longer run smoothly, they
don't walk, [they crawl][github-slowness]. The operating systems are
[breaking basic shutdown and boot][windows-brick]. AI slop on social platforms is
actively manifesting the hyperstition of the [Dead Internet Theory
][dead-internet-theory] into reality.  Most of all, it's clear [you are the
product, even if you're paying for it][you-are-the-product]. With software as a
whole moving in a decidedly anti-user direction, it's little wonder why
almost everyone I know has been deeply dissatisfied with the tech they use,
myself included.

It is from this frustration that the idea of ***digital minimalism*** has started
to gain signficant traction. Digital minimalism centers around the idea that your
use of tech should be guided by what is truly important to you. For some, this
may be as extreme as the aforementioned /g/oblins, shunning all new tech
like the plague. For others it may be going as far as to use a dumbphone over a
smartphone. For me, digital minimalism comes in the form of asking: why I use a
certain technology? What it costs to use? My money? My attention? *My humanity?*
If the cost isn't worth the benefits, are there alternatives? Do I
need to use this tech all the time? Does the tech need to have access to this
specific device?  etc. etc. Digital technology that I can afford to live without
should be removed, and that which must use will have only the core functionality
I need extracted and nothing more.

For example, like many, I've had a very negative and addictive experience
with social media platforms in the past. For me, that was YouTube. At one point,
I was watching upwards of 3+ hours of it per day during the COVID lockdowns.
Initially, I started by marking channels as "Do not recommend" on the worst
offenders abusing the recommendation algorithm, yet I still watched way too much
for my liking. I then disabled my watch history and cleared it completely.
YouTube stopped putting hyper-individualized recommendations, and that ensured I
got off of the platform quickly. I still found myself clicking on a few
additional videos here and there and occasionally reading the banal and
idiotic comments. That made me go back and question: why do I *need* to use
YouTube? The answer I found was that it was a useful hosting platform for all
kinds of videos, and that I really only needed to watch specific videos on it
that I was explicitly looking for, or was linked to me by my friends. This
was the original use of YouTube in 2006, and it still remains core to why I
continue to use it. My solution? Use [mpv][mpv] with [yt-dl][yt-dl] to extract
just the video, and watch it in isolation with zero distractions or
continuations. Then force every YouTube link on my machine to open this way
with [handlr-regex][handlr-regex]. After disabling the YouTube app on my phone,
this is the only way I'll watch YouTube videos.

Is this for everyone? No, it just needs to work for me. Won't this break
regularly? Probably, it's in Google's interest to break this (ab)use of their
platform at every opprotunity. Isn't it inconvenient? Yes, that's sort of the
point. If convenience is what got me into that doomscrolling rut, the only way
out requires deliberately choosing the inconvenient option.

<!--Socially, practicing digital minimalism feels like your living as an ascetic in-->
<!--modern society. One [Wired author][wired] struggled to connect with-->
<!--their friends that have switched to a dumbphone, likening it to being mentally-->
<!--disabled. To which, I don't fully disagree. You're less connected than you were-->
<!--before. I stopped using Facebook in 2016, Twitter in 2024, and never used-->
<!--Instagram or TikTok. I'm by no means up to date with the latest memes, slang, or-->
<!--what have you. My younger friends call me a boomer for not being in touch, yet-->
<!--I'm mentally sharper, better read, less easily swayed by passerby trends or-->
<!--propaganda, and generally have a healthier outlook on life than any of them.-->

As a developer, digital minimalism seems to reflect the intent of the original
Unix philosophy: "Make each program do one thing well." Things have certainly
changed signficantly since the 1970s, but its clear how much of modern software
isn't even focused on the primary task at hand. How much telemetry and logging is
in each JavaScript blob we download on the web? How much of Windows for consumers
is doing tasks for the

This is all to say

[mpv]: https://mpv.io/
[yt-dl]: https://github.com/yt-dlp/yt-dlp
[handlr-regex]: https://github.com/Anomalocaridid/handlr-regex
[wired]: https://www.wired.com/story/dumbphone-owners-have-literally-lost-their-minds/
[windows-brick]: https://www.windowslatest.com/2026/01/25/microsoft-suspects-some-pcs-might-not-boot-after-windows-11-january-2026-update-kb5074109/
[github-slowness]: https://bsky.app/profile/chrisbiscardi.bsky.social/post/3mdbovetejk2g
[dead-internet-theory]: https://en.wikipedia.org/wiki/Dead_Internet_theory
[you-are-the-product]: /blog/2026/01/23/you-are-the-product-period
