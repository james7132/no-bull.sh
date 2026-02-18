+++
title = "In Search of a Discord Replacement"
path = "blog/2026/02/16/in-search-of-a-discord-replacement"
date = "2026-02-16"
updated = "2026-02-18"

[taxonomies]
tags = ["Discord", "Self-hosted", "Privacy", "Open Source"]
+++

I've really liked Discord. I'm one of the early adopters from 2016 and
enthusiastically convinced my friends and communities to move to it. Since then,
I've developed a moderation bot. I helped build multiple communities of 10,000+
users. I've made lifelong friends, helped build FOSS projects, and organized
events and grassroots movements. For the past 10 years, Discord has been
extremely useful and borderline irreplacable throughout many facets of my life.

However, since the start of the pandemic, my friends and I have watched the slow
but inevitable degradation of service, unfixed bugs, and watching the company
deseperately flail about trying to achieve profitability. Each time we'd
encounter some kind of bug, the voice chat I frequent would be flooded with cries
of "We've ***GOT*** to get off Discord." Each time this happens, I'd look into
alterantives, maybe try one out, but never really pull the trigger on migrating
to an alternative.

On Febuary 9th 2026, Discord announced that it would be [universally requiring
age verification][discord-age-verification]. This follows a series of laws passed
in various jurisdictions around the world requiring age verification for access
to potentially sensitive content. This has required most online platforms to
partner with third party vendors for verifying users' government IDs... which
have been [leaked en masse][discord-id-leak]. In their infinite ~~wisdom~~ greed,
Discord, decided to enforce this requirement universally instead of just the
jursidiction where it's legally required.

Many users, myself included, view this as a major breach of trust and the final
stage of years of gradual enshittification. It's lit a fire under our ass to
finally figure out a migration plan away from Discord. Documented below are my
general findings and suitability for the communities I help run.

# Requirements
My review and analysis is only for the communities I help run, and while I think
the requirements are similar for most communities currently on Discord, they may
not hold for everyone. There are three types of communities I participate in and
help run:

**Large centralized online communities** - I help run
[discord.gg/touhou](https://discord.gg/touhou), one of the largest Touhou fan
communities on Discord. At time of writing, there are 55,000+ members in the
server, with more than 2,000 active weekly active users. Orbiting it are a number
of smaller targetted communities focused on different facets of the community,
such as [Touhou Wiki](https://touhouwiki.net), [Gensokyo
Radio](https://gensokyoradio.com), and various other niche communities.
These tend to be a central gathering space for those in the community without any
one particular central goal in mind, often acting as just an online [third
place](https://en.wikipedia.org/wiki/Third_place) where members of a shared
interest community can come together and openly discuss various topics. Many of
these make heavy use of Discord's voice channels, video chat, and screensharing.
These servers have a hard requirement for adequate moderation tools for dealing
with any bad actor willing to join the community.

**Large productivity oriented communities** - This includes the [Bevy
Discord](https://discord.gg/bevy) and various FOSS development related servers.
While these also act as a social gathering place, there is also a targetted
productivitiy oriented goal associated with these servers.  These servers also
have a hard requirement for adequate moderation tools for dealing with any bad
actor willing to join the community.

**Small friend group chats** - These servers tend to be much smaller, topping off
at only a few tens or hundreds of members. Unlike the others, most of the members
of these groups already have a decent understanding of the other people in the
server, and moderation tools are thus not a hard requirement.

---

The following are what I would consider hard requirements that are
non-negotiable:

 - **Discord-like Onboarding UX** - The greatest issue with bulding community
   comes from the experience of new users.
 - **Multiple text and voice chat channels** - The communitiies I help run need
   to support thousands of users there needs to be a way to support organized
   threaded chats.
 - **Decent Mobile Experience** - A mobile app shouldn't be required, and a
   progressive web app (PWA) might be acceptable in the interim, but
   allowing users to access the chat from a mobile phone is a strict requirement
   for community engagement nowadays.
 - **Self-hostable** - The laws that prompted the need for age verification still
   apply in target jurisdictions, and relying on large platforms that are easy
   targets for lawsuits will just result in the community hopping from platform
   to platform.

There is also a short list of "nice to have" features:

 - **Free and Open Source (FOSS)** - This relates heavily to self-hosting, but
   having direct source code access helps the community contribute back and
   build a better experience together.
 - **Minimal Vibecoding** - In the wake of Discord's announcement, there's been a
   glut of opportunistic vibecoders trying to steal marketshare. While the vast
   majority of them can be easily ruled out, there's a small handful of projects
   that have some level of plausible deniabilty. While vibecoding isn't a hard
   dealbreaker, it poses a serious question of whether the application
   can be trusted to be properly maintained into the indefinite future.
 - **End-to-end Encryption** - Privacy is important! It would be nice to have 1:1
   DMs and small group chats support end-to-end encryption. Supporting it for
   large communities of thousands of users might not be the best idea though.
 - **TTL-ed messages** - In line with the prior point about E2EE is the support
   for TTL'ed messages. Some of the servers I'm in are up to 10 years old, and
   have discussions that should have long been discarded. A TTL that is too short
   (i.e. 14 days) may be untenable, but a decently long TTL of a year or more
   might be acceptable.
 - **Screensharing and video chat** - Some of the communities I help run are
   heavily reliant on screensharing for shared activities (i.e. group watches,
   group gaming, raiding, etc.) It would be nice, though not strictly required,
   to support screensharing and video chat.

# Non-Starters
Let's start off by ruling out some major players in the space that are strict
non-starters:
 - **Good ol' [IRC](https://en.wikipedia.org/wiki/IRC)** - The onboarding experience is not well suited for modern
   communities. Needing to have someone set up an IRC bouncer for non-technical
   users is already a non-starter.
 - [**Telegram**](https://telegram.org/) - Cannot be self hosted. Ties to the
   [Russian government][telegram-government] make it a serious security concern.
   Not FOSS.
 - [**WhatsApp**](https://www.whatsapp.com/) - Cannnot be self-hosted, does not
   support multiple text and voice chat in large communities. Not FOSS. Meta's
   ownership also raises more privacy concerns than it resolves.
 - **[QQ](https://im.qq.com/index/), [WeChat](https://www.wechat.com/en/)** -
   Cannot be self-hosted. Ties to the [Chinese government][wechat-government]
   make it a serious security concern. Not FOSS.
 - [**LINE**](https://www.line.me/en/) - Cannot be self-hosted, does not support
   multiple text and voice chat in large communities. Not FOSS.
 - [**Steam Chat**](https://steamcommunity.com/chat) - Not self-hostable. Not
   FOSS. All chat has a very low TTL of only two weeks. It has text and voice chat
   and screensharing, but does not have video chat.
 - **[Slack](https://slack.com/),
   [Microsoft Teams](https://www.microsoft.com/en-us/microsoft-teams),
   [Google Chat](https://chat.google.com/)** - Cannot be self-hosted.  Not well
   suited for large communities of thousands of users due to per-user monthly
   costs. Limited message history on free edition. Not FOSS.
 - [**Rocket.chat**](https://www.rocket.chat/) - Self-hostable, FOSS, has a rather
   nice feature set, but voice calls are only available for
   [enterprise customers][rocketchat-pricing]???  Free version limited to only 50
   users. Need to contact support to enable more.
 - [**Teamspeak**](https://www.teamspeak.com/en/) - Self-hostable, not FOSS. Has
   a mobile app. Free license is limited to only 32 users. 1024 users for
   $500/year.
 - [**Root**](https://www.rootapp.com/) - Not open source. Not self-hostable.
   Does not have a publicly accessible mobile app.
 - [**Guilded.gg**](https://www.guilded.gg/) - Not open source. Not
   self-hostable. Never had a mobile app? Bought out by the pedophile platform,
   Roblox. No longer exists.
 - [**Echoed.gg**](https://echoed.gg/) - Not open source. Not self-hostable.
 - [A](https://github.com/areoseek/CutTheCord)
   [multitude](https://github.com/dmccoystephenson/accord-prototype) of
   [opportunistic](https://github.com/WAN-Ninjas/AmityVox)
   [vibecoding](https://github.com/ancsemi/Haven)
   [asshats](http://github.com/blitechat/BLITE)
   trying to stake out a name for themselves.

## Matrix
Barring IRC and XMPP, [Matrix](https://matrix.org/) is probably been one of the
longest lived FOSS chat options out there. Its 2.0 featureset seems to match up
with everything we want and more.

However, self-hosting Matrix is a genuine pain in the ass. Synapse is a resource
guzzler beyond compare. An *idle* single-user instance uses 4GB of RAM. Its
replacement, [Dendrite](https://github.com/element-hq/dendrite), is
simultaneously vaporware and maintainence mode. Dendrite's replacement, [Synapse
Pro](https://element.io/en/server-suite/synapse-pro), isn't really self-hostable
and is closed source. Arguably made just to grift EU governments out of their
money.

The true dealbreaker, though, has to be the new user experience. We tried
registering multiple users onto a self-hosted instance, and found that all
clients but Element's latest and greatest failed to support all of the features
described in the protocol. The end-to-end encryption periodically broke and
rendered chat history completely inaccessible.

We also tried the more resource efficient home server implementations like
[Conduit](https://conduit.rs/) and its fork
[Conduwuit](https://github.com/x86pup/conduwuit), but that exacerbated the
combinatorial feature support woes even more. Instead of just N different
clients having problems with one home server, we now had M different server
implementations combined with said N clients for a whole N-by-M compatibility
matrix of problems. All of this just so a brand new user to get started chatting
with their friends. Apparently there's now
[Tuwunel](https://matrix-construct.github.io/tuwunel/) and
[Continuwuity](https://continuwuity.org/), but I'm too burnt out on Matrix as a
whole to try to bark up that tree.

Matrix has been around for 10+ years and has had major corporate backing, yet its
UX still feels worse than any alpha-quality options on this list, including some
of the clearly vibecoded projects that have been recently announced. This is
truly an abysmal dogshit state of affairs for such a platform. It's almost like
the devs at Element and the greater Matrix community wants the experience to
remain as broken as it is now.

EDIT: Not even 24 hours after this post was published, a [scathing 
report](https://soatok.blog/2026/02/17/cryptographic-issues-in-matrixs-rust-library-vodozemac/)
came out detailing multiple side-channel vulnerabilities in Matrix.org's Vodozemac
library powering Matrix's E2EE feature. I'm no cryptography expert and cannot
evaluate the finer technical claims of the article, but the way Matrix.org 
handled this report on a person-to-person basis is deeply unprofessional. It's
really disappointing to see, and is pushing me even further away from it as
a platform.

## Signal
[Signal](https://signal.org/#signal) is *the* E2EE chat app and protocol. It's
FOSS software, and can be
[self-hosted](https://github.com/signalapp/Signal-Server) (though with much
difficulty). It supports text, voice, and video chat, and the desktop option
supports screenshare, though it's closer to Skype's older model where there is a
single channel of discussion and a call will notify everyone in the chat. Signal
also comes with a high quality and accessible mobile app, and is arguably
developed with a mobile-first approach.

Signal is stunningly solid option for small groups and one-to-one chats, but I
would caution against building any particularly large community on the platform.
Signal, by default, supports up to 1,000 users in one group chat, but anyone
using Discord right now knows how unruly that can be.

## Fluxer.app
[Fluxer.app](https://fluxer.app/) is a rather promising option, directly aiming
to replace Discord. It's clearly developed with the intention of being a direct
replacement for Discord's service, and has monetization built in from the get go.
It seemingly has all of the features we expect out of Discord out of the box, and
is free and open source software under AGPLv3.

The project is really new, only being announced and open sourced within the last
month. The entire project is 1.5 million lines of code and there is no git history
prior to open sourcing. The author claims that they did not [vibecode
it](https://blog.fluxer.app/how-i-built-fluxer-a-discord-like-chat-app/) and they
did the "normal" practice of squashing history when making an initial release,
but I feel like that is just a plausibly deniable excuse, and will need to wait
and see if they actually follow through with it. They're currently not accepting
that many PRs due to a "ongoing codebase-wide refactor", and, for the same
reasons, self hosting instructions are currently missing as a whole.

One potential concern is that Fluxer.app is licensed under AGPLv3 with a CLA.
This isn't an uncommon combination to see used in FOSS rugpulls where the owner
of a project takes it closed source, typically forcing a community fork in the
process. This isn't usually a hard dealbreaker, but I would rather not risk the
headache of a secondary migration from losing trust yet again.

## Sharkord
[Sharkord](https://sharkord.com/) is a relatively new FOSS project with the aim
to be a direct Discord replacement. It supports basic text chat, voice chat,
video chat, and no-audio screensharing at this current time. It was relatively
easy to self host.

However, due to how new it is, it's currently riddled with bugs, and currently
does not have a mobile app or PWA support. It's unclear whether this is the
result of vibecoding or just general developer incompetence. Given the [author's
comments](https://www.reddit.com/r/selfhosted/comments/1r08bd8/comment/o4l2tr0/)
on use of AI for the interface and their clearly AI generated profile
pic on GitHub, there's a high likelihood that a non-insignificant amount of the
app was vibecoded and calls into question if they can be trusted to actually
maintain the app long term.

## Stoat (formerly Revolt)
[Stoat](https://stoat.chat/) was the option I tried long before any of this
chaos, and honestly the one I'm rooting for the most. It aims to be a direct
replacement for Discord. It's FOSS and is self-hostable. It supports text chat,
and previously supported voice chat until they decided to rewrite the backend for
audio. It's never supported video chat or screensharing, and does not have a
usable mobile app yet.

It's also set up such that self-hosting includes infrastructure for all of
Discord. You can have the equivalent of multiple Discord servers on the same
self-hosted instance. This poses some extra headache for the admins, as users can
hide discussions that are out of reach of moderators or system administrators.

Unfortunately, the development pace has not kept up and many of the missing
fundamental features are not currently present.

## Spacebar (formerly FOSScord)
[Spacebar](https://spacebar.chat/) is a project trying to create a 1:1 version of
of Discord down to the API calls being made. They have a custom client and server
that can work with each other or be used with Discord's official API. It's all
FOSS and self-hostable.

However, due to its nature in attempting to replicate Discord 1:1, it lacks a
mobile app. At time of writing, it seems like Spacebar does not support anything
tied to a voice channel in Discord.

## XMPP (with Fluux Messenger)
[Fluux Messenger](https://github.com/processone/fluux-messenger) from ProcessOne
is a XMPP frontend that looks awfully like Discord. Any backing XMPP server can
be used with it, such as ProcessOne's
[ejabberd](https://github.com/processone/ejabberd). This should cover text chat
like Discord fairly well, but will require additional effort to support an
integration with Jitsi for voice, video, and screenshare.

Fluux Messenger also has the same licensing issues as Fluxer.app. It's also
AGPLv3 with a CLA, but thankfully XMPP is an open protocol so any adequate
frontend can be used as a substitute.

## Mumble
[Mumble](https://www.mumble.info/) is a FOSS, self-hostable, VoIP software and is
made to be close to Teamspeak in UX. It's created with a desktop use case in mind
but there are compatible third party mobile apps. Its voice channels are
structured close to that of Discord's, where users can hop in and out at any
time, and the channels exist independently from any single given call. It's a
voice chat-first application with some level of support for text chat for those
in a voice channel. Joining a server requires actively joining a voice channel.
Unlike Discord, the text chat does not have long term text chat history. I think
this is appropriate for a text chat that is purely supplemental to a voice chat,
but that It does
not support video chat or screensharing.

## Zulip (w/ Jitsi)
[Zulip](https://zulip.com/) is a fully open source FOSS chat application that can
be self hosted. What differentiates itself is the high number of integrations it
has with other services. Most notably, it has a frontend integration with Jitsi,
which support voice, video and screenshare. It has a usable mobile app.

As a text chat, it's probably the most complete and solid experience out of all
of the options in this list. Zulip's threading model, or "topics" as they're
called in Zulip vernacular, take getting used to, as every conversation is in a
topic, and each channel does not have a top level discussion that can be branched
from.

The Jitsi integration as it currently stands does not act like Discord's voice
channels, where users can hop in and out at any time, but are tied to established
calls tied to messages sent in a text channel. This might be viable in a
productivity oriented community like FOSS development groups, but this may not be
a good fit for large general purposes communities.

# Conclusion
Overall, I'm not too happy with the state of the viability of many of these
alternatives. Many options have been around for 10+ years, and still do not come
close to the convinence provided by Discord.

Thus far, out of all of the options I've reviewed, Zulip, with Jitsi, might be
the best immediate fit for the requirements outlined in this post. It seems like
it ticks all of the boxes for a usable UX, solid self-hosting support, has a
usable set of cross-platform clients, and seems to support all of the immediate
fundamental features most Discord communities are used to. Its model isn't a
great 1:1 fit with what users expect out of a Discord server and its interface
is definitely oriented for use as a business oriented chat, but, given enough
time, I think most users could become accustomed to its use.

Fluxer.app might be a viable alternative in the future, as its feature set
aims to directly compete with that of Discord's. However, the intent on
monetization and lack of FOSS engagement, poor self-hosting support, and
questionable licensing decisions casts doubt on its long term viability. In the
case of a FOSS rugpull (a la [Emby vs
Jellyfin](https://jellyfin.org/docs/general/about/#why-did-you-fork)), I'm sure
the community will be able to pick up the slack eventually, but that may be way
too far out to consider for now, and I would rather not do a secondary migration
in the case of such an event.

That's it for now.  As I try more alternatives, I'll be sure to update this post
with my observations. I don't think it's practical to migrate very large
communities at the current moment, but keeping an alternative around in case shit
really hits the fan may be a viable migration path forward.

# Acknowledgements
This blog post was researched and edited by the following members of the
discord.gg/touhou community: Shio, ReUKing, Great Sage, Jordy, Mami,
Photographicrat, and Ember.

# Appendix: Summary Table

|Name|FOSS|Self-host|Mobile|Text|Voice|Video|Screenshare|Notes|
|:---|:---|:--------|:-----|:---|:----|:----|:----------|:----|
|Matrix|✅   |✅    |✅[^1]|✅  |✅   |✅   |✅         | Poor user UX.
|Sharkord|✅ |✅    |❌    |✅  |✅   |✅   |✅         | Really buggy, possibly vibecoded
|Fluxer.app|✅|❌   |❌[^2]|✅  |✅   |✅   |✅         |
|Stoat |✅   |✅    |❌    |✅  |❌   |❌   |❌         | Low dev velocity.
|XMPP  |✅   |✅    |✅[^1]|✅  |❌   |❌   |❌         |
|Jitsi |✅   |✅    |✅    |❌  |✅  |✅    |✅         |
|Zulip |✅   |✅    |✅    |✅  |❌   |❌   |❌         |
|Spacebar|✅ |✅    |❌    |✅   |❌  |❌   |❌         |
|Mumble |✅   |✅   |✅[^1]|✅  |✅   |❌   |❌         |
|Signal|✅   |✅    |✅    |✅  |✅   |✅   |✅         | Poorly suited for large communities.
|Rocket.chat|✅   |✅|✅   |✅  |✅   |✅   |✅         | Free instance limited in the number of users.
|IRC |✅  |✅       |✅[^1]|✅  |❌   |❌   |❌         |
|Telegram|❌  |❌   |✅    |✅  |✅   |✅   |✅         |
|WhatsApp|❌  |❌   |✅    |✅  |✅   |✅   |✅         | Poorly suited for large communities.
|QQ      |❌  |❌   |✅    |✅  |✅   |✅   |✅         |
|WeChat  |❌  |❌   |✅    |✅  |✅   |✅   |✅         |
|LINE    |❌  |❌   |✅    |✅  |✅   |✅   |✅         | Poorly suited for large communities.
|Teamspeak |❌  |✅ |✅    |✅  |✅   |✅   |✅         | Limited in the number of users.
|Steam Chat|❌  |❌ |✅    |✅  |✅   |✅   |✅         | Maximum 2 week TTL on messages
|Slack|❌  |❌      |✅    |✅  |✅   |✅   |✅         | Maximum 90 day TTL on messages (Free edition)
|Microsoft Teams|❌ |❌|✅ |✅  |✅   |✅   |✅         |
|Google Chat|❌  |❌|✅    |✅  |✅   |✅   |✅         |
|Root       |❌  |❌|✅    |✅  |❓   |❓   |❓          |
|Guilded.gg |❌  |❌|❌    |❌  |❌   |❌   |❌         |
|Echoed.gg |❌  |❌ |❌    |✅  |✅   |❓   |❓         |

[^1]: Requires one of the many community made mobile apps, feature support might
    be inconsistent.
[^2]: No mobile app but there is PWA support.

[discord-age-verification]: https://discord.com/press-releases/discord-launches-teen-by-default-settings-globally
[discord-id-leak]: https://www.bbc.com/news/articles/c8jmzd972leo
[telegram-government]: https://www.newsweek.com/telegram-messenger-russia-fsb-ties-report-2083491
[wechat-government]: https://citizenlab.ca/research/we-chat-they-watch/
[rocketchat-pricing]: https://www.rocket.chat/pricing
