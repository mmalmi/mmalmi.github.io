---
layout: post
title:  "How To Fix Everything That’s Wrong With the Internet"
date:   2019-11-04 13:37:00 +0000
tags: decentralization economics iris
image: https://siriusbusiness.fi/assets/images/posts/internet-broken.jpeg
---
![Cover](/assets/images/posts/internet-broken.jpeg)

What do Google, Facebook, Youtube, Amazon, Uber and a phone book have in common? They are **indexes** — searchable lists of stuff. Google is a list of keywords mapped to the websites they appear in. Facebook is a list of profiles, posts, private messages, events and other types of information. Youtube has users, videos and comments. Amazon: merchants and items. Uber: drivers, customers and ride requests.

Oh, and the phone book. Young readers might not know that it was a 20th century business model where you print out a database of names matched with phone numbers and drop the heavy object into people’s mailboxes.

Most online unicorns are essentially just indexes with a nice user interface and occasionally some sort of customer support. They are commonly called “platforms”.

Strong network effects are the boon or bane of indexing, depending on whom you ask. Winner takes it all: users must join the most popular index in order to find others and be found, i.e. to get the most search results and appear in as many searches as possible.

This is good for the winning company’s shareholders. “Competition is for losers”, as Peter Thiel wrote in his book “From Zero to One”. Also, it’s convenient and computationally efficient when you need to search only one index which contains everything and runs in a highly optimized data center.

The downside is that these companies become central points of tremendous power — in other words, **single points of failure**. Many of them have become necessities that our daily lives and livelihoods depend upon, yet they are not accountable to their own users. They are private companies that can quite freely favor or discriminate against whomever they like. What is your recourse when Facebook decides to suspend your account for 1 month at a critical time?

There have been [calls](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3220737) to regulate online platforms [as public utilities](https://en.wikipedia.org/wiki/Social_media_as_a_public_utility) akin to banks or electricity companies. Good regulation could help, but bad regulation could make things worse. Many things can go wrong when trying to solve problems by government force. Government too is a monopoly — one that you can’t even unsubscribe from when things go wrong. And how did it work out with bank regulation? It’s always safer if we can develop new technology that solves these problems without the use of force (and more ethical, one could argue).

What Satoshi Nakamoto wrote about banks applies to online platforms as well:
> “The root problem with conventional currency is all the trust that’s required to make it work. The central bank must be trusted not to debase the currency, but the history of fiat currencies is full of breaches of that trust. Banks must be trusted to hold our money and transfer it electronically, but they lend it out in waves of credit bubbles with barely a fraction in reserve. We have to trust them with our privacy, trust them not to let identity thieves drain our accounts.”

As we have already seen, such central points will inevitably be abused from the inside or outside for commercial, political or outright criminal gain, while the rest of us pay the price.

Historically, printing presses, telegraph offices and railway stations have been some of the first central points seized by communist revolutionaries. Modern day authoritarians hijack search engines and social media corporations. They can be used to direct or suppress public debate and are [globally used](https://www.oii.ox.ac.uk/news/releases/use-of-social-media-to-manipulate-public-opinion-now-a-global-problem-says-new-report/) to influence politics.
Some political activists demand “[deplatforming](https://en.wikipedia.org/wiki/Deplatforming)” of people they disagree with — too often successfully. Big tech companies themselves [admittedly](https://thehill.com/policy/technology/402495-twitter-ceo-jack-dorsey-i-fully-admit-our-bias-is-more-left-leaning) have a bias against conservatives, which they have [arguably](https://quillette.com/2019/02/12/it-isnt-your-imagination-twitter-treats-conservatives-more-harshly-than-liberals/) acted upon, banning them more often than left-wing users.

In 2018 Germany [started enforcing a law](https://www.bbc.com/news/technology-42510868) that obliges social media companies to censor “obviously illegal” user content within 24 hours or face penalties up to 50 million euros. Human Rights Watch [criticized](https://www.hrw.org/news/2018/02/14/germany-flawed-social-media-law) the law on the grounds that it “can lead to unaccountable and overbroad censorship” and “sets a dangerous precedent for other governments”. At least Russia, Singapore, and the Philippines have cited the law as a positive example of legislation for removing “illegal” content online. France enacted a [similar law](https://www.theguardian.com/world/2019/jul/09/france-online-hate-speech-law-social-media) in 2019.

A topic of their own are authoritarian countries such as China, Iran, Turkey and North Korea which severely restrict the access to social media or even to the whole internet. People in those countries resort to VPNs, file sharing by [usb sticks](https://www.abc.net.au/news/2017-12-03/north-korea-activists-sneak-films-music-usb-drives-regime-change/9210928) or occasionally [bluetooth mesh networks](https://www.forbes.com/sites/johnkoetsier/2019/09/02/hong-kong-protestors-using-mesh-messaging-app-china-cant-block-usage-up-3685/).

For many people, Snowden’s revelations about NSA mass surveillance programs have been the wake-up call to **privacy** issues. It’s reasonable to ask if we want to share our digital lives with the big tech and subsequently the government.

Another concern about centralization is **infrastructure security**. What if someone at Google just messes up? What if WhatsApp servers are unreachable in an emergency? That concern can be shared regardless of your particular political bias.

**How do we make it right?** Decentralize indexing. Take out the middleman. It gets a bit more technical here.
Bitcoin is a proven decentralized alternative to central banks and money transmitters. We no longer have the situation where Alice wants to send money to Bob via middleman Carl, but Dave prevents it by pressuring Carl. Alice (or [Alexei](https://www.coindesk.com/russian-opposition-leader-raises-3-million-in-bitcoin-donations)) doesn’t need anyone’s permission to send her own bitcoins to Bob. Now we just need to make bitcoin more convenient for everyday use and [hodl](https://en.wikipedia.org/wiki/Hodl).

Bitcoin and other decentralized **ledgers** are all about state management: how to achieve a consensus on the ledger’s balances without asking a central authority. Bitcoin presented a novel solution to the problem: **blockchain** — or more specifically, **proof of work**. Every full bitcoin node replicates a chain of transaction blocks, and the valid version of the chain stamped by the most computing power (proof of work) is considered the consensus.

However, **decentralized _indexes_ face a different set of technical challenges and tradeoffs**. For example, **blockchain is not the right tool for social media**: you don’t need or want slow and expensive perfect synchronization with everyone in the world. Eventual consistency is sufficient and can be achieved with [conflict-free replicated data types](https://en.wikipedia.org/wiki/Conflict-free_replicated_data_type): systems that don’t even need an internet access — just occasional contact with peers. Examples of such systems are [Gun](https://github.com/amark/gun), [Automerge](https://github.com/automerge/automerge) and [OrbitDB](https://github.com/orbitdb/orbit-db).

![CAP theorem](/assets/images/posts/cap-theorem.png)

*CAP theorem: Consistency, Availability and Partition-tolerance — choose two. In a decentralized system one of the two must be partition-tolerance — network failures do happen.*

When network failures inevitably happen, you need to choose between availability and consistency of state. In case of a trustless ledger, it may be better to sacrifice availability and stop transactions in order to prevent double-spending. Social networks and many other applications might do fine without strong consistency, i.e. everyone always having the same dataset. The content you post offline can be synchronized later. Even bank ATMs choose A over C, since the benefits outweigh the risks (as explained in this excellent [article](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed/) on CAP).

Another challenge is **how to make sure that the data you receive from peers is relevant or valid**. You don’t want spam in your social media feed. You want search results to actually contain the searched words. When the index is not run by a single trusted entity, you can use a **web of trust** to filter out users and peers that produce spam or other unwanted content — all without giving power to central moderators.

Bittorrent solves this somewhat similarly, exchanging file parts with peers on tit-for-tat basis, rewarding peers for co-operation. You can see your download start slowly and then speed up as other downloading peers see that you are giving back.

![Network traffic report by Sandvine](/assets/images/posts/sandvine-report.png)

*According to a [report](https://www.sandvine.com/hubfs/downloads/archive/2011-1h-global-internet-phenomena-report.pdf) by Sandvine, bittorrent traffic accounted for over 50% of upstream broadband traffic in North America in 2011.*

Sharing of static files in a peer-to-peer network is old and proven technology. However, **maintaining and querying decentralized indexes** — big dynamic datasets — **is easier said than done**. Centralized torrent indexes are the single point of failure that governments, defending billion-dollar corporate interests, have heavy-handedly cracked down upon — most famously [The Pirate Bay](https://en.wikipedia.org/wiki/The_Pirate_Bay) and more recently [KickassTorrents](https://en.wikipedia.org/wiki/KickassTorrents).

[Torrent Paradise](https://torrentfreak.com/torrent-paradise-creates-decentralized-pirate-bay-with-ipfs-190120/) takes torrent indexing in a more decentralized direction. While the index is still centrally maintained, it is distributed via [IPFS](https://ipfs.io/) which makes finding its maintainer or preventing its distribution more difficult. The index maintainer could even hide behind Tor to prevent detection by traffic analysis.

[OpenBazaar](https://openbazaar.org/) is a fairly popular IPFS-based project that lets merchants index their own products. [YaCy](https://yacy.net/), founded in 2006, is a fully decentralized web search application. Both are based on [distributed hash tables](https://en.wikipedia.org/wiki/Distributed_hash_table), the same technology that bittorrent uses for peer finding.

[Manyverse](https://www.manyver.se/) is an interesting offline-first mobile application that can synchronize over bluetooth, wifi or remote servers. It is based on the Scuttlebutt feed synchronization system, which already has hundreds of active users.

I have been working on [Iris](https://github.com/irislib/iris/blob/master/README.md), **a social networking application that stores everything on its users’ devices and connects to peers directly**. Interface-wise it’s not too different from some existing social media — you can post text, photos, videos, audio or other types of files into your feed.

You can have end-to-end encrypted private chats and get mobile or desktop notifications. Users give each other trust ratings to form a web of trust — a concept that has been used in public key infrastructure since the 90s. Trust ratings are functionally not too different from adding a friend or following someone.

![Iris Social screenshot](/assets/images/posts/iris-social-screenshot-2019.png)

*Iris [browser application](https://github.com/irislib/iris-angular). Also available for [desktop](https://github.com/irislib/iris-electron), [mobile](https://github.com/irislib/iris-mobile) and as a [library](https://github.com/irislib/iris-lib).*

Iris web of trust works both on the software level and the user level. On the software level it is used to manage peer connections and prioritize storage space: friends connect to each other and replicate each other’s content. On the user level it aims to serve as a [socially scalable version of the system of trust](https://siriusbusiness.fi/learning-to-trust-strangers) that naturally exists in tribes and villages, reducing the need for a [centralized](https://siriusbusiness.fi/law-is-better-without-monopoly) justice system and facilitating the [gift economy](https://en.wikipedia.org/wiki/Gift_economy).

Web of trust helps filter out spam and other unwanted content without entrusting the power to a central moderator. Instead of a single moderator, you have multiple “moderators” whom you can choose and whose collective decisions you can override. **It makes trolling, fake news and other propaganda campaigns more difficult**, since your messages are only shown to people whose WoT you are in.

Based on attestations (“identity verifications”) from your WoT, **Iris maps natural names to public keys and other identifiers, providing a decentralized alternative to digital identity providers** such as domain names, email addresses, phone numbers, social media handles or CA certificates. Similarly to [Petnames](https://web.archive.org/web/20120204092248/http://www.skyhunter.com/marcs/petnames/IntroPetNames.html) or Namecoin, it fulfills all three properties of Zooko’s triangle outlined in [Names: Decentralized, Secure, Human-Meaningful: Choose Two](https://web.archive.org/web/20120204172516/http://zooko.com/distnames.html).

Unlike Namecoin addresses or other global names, Iris names are not globally unique: there can be multiple people named John Smith. When searching for a name, you get a dropdown list of results ordered by their WoT distance, along with avatars and other human-meaningful attributes that are attested by your WoT. **Iris doesn’t have a globally shared state. Instead, what you see depends on what your WoT says**.

It could be even used to maintain a shared conception of borders, countries and properties. Instead of Google [playing the geopolitical moderator](https://www.newsweek.com/googles-place-geopolitics-493769), the borders and names you see on a map would depend on what your WoT has attested to. Good for local sovereignty advocates. Use together with [uncensorable](https://www.nytimes.com/2017/09/20/world/europe/catalonia-referendum-spain.html) public polls.

Ideally, Iris users would have device-based private keys that share access to the same private data. Losing one key doesn’t matter, and the other keys can be used to invalidate the lost one. If you lose all your keys, you can just ask your WoT to attest a new key to your identity. After enough verifications, other users can fetch the private chats with your old key and re-encrypt them to the new key. Your non-shared private data would be lost though. That could be avoided with yet another key recovery option: [Shamir’s Secret Sharing](https://en.wikipedia.org/wiki/Shamir%27s_Secret_Sharing), which allows e.g. 3 out of 5 recovery shards stored by friends to restore your private key.

![Iris mobile app](/assets/images/posts/iris-react-native-2019.png)

*End-to-end encrypted private chat in the [Iris mobile app](https://github.com/irislib/iris). The strategy is to start with private messaging, since it doesn’t require the same critical mass as public messaging.*

Iris outsources storage and networking to Gun, the aforementioned CRDT system. With storage adapters it provides offline-first eventually consistent data synchronization between all kinds of storages, such as RAM, file system, local area network peers (multicast), websocket servers or remote WebRTC peers. With a bluetooth adapter you could use it in an ad hoc mesh network where peers don’t even need to be connected all the time — very censorship-resistant.

Iris users maintain their own **indexes** of Message and Contact objects. These are synchronized and queried over Gun. When you search for messages or contacts, other indexes in your web of trust are also queried. That is **web of trust based decentralized indexing**.

This works using Gun’s simple API:
```
# open our own index (read & write permissions)
user = gun.user()
user.auth(keypair)
user.get(‘messages’).get(indexKey).put(message)
user.get(‘messages’, params).map(msg => doSomething(msg))
user.get(‘contacts’)...

# open someone else’s index (read-only)
user = gun.user(publicKey)
user.get(‘messages’, params).map(...)
```

**The same paradigm could be used to store and retrieve other kinds of objects and build all kinds of decentralized alternatives to platforms** like Google, Amazon, Uber etc.

Sharding, replication factor, algorithms for efficient querying of peers and other optimizations are yet to be explored. Perhaps a distributed hash table between trusted peers could be used. The optimal division of labor between local devices and servers (super-peers) needs further research: you want it to work offline or in a mesh network (to some extent), but also to be able to utilize the power of data centers.

Servers and efficient data centers have their place even in a system where the data model, storage and networking support decentralization. You could still have companies that maintain large indexes: they would just be interoperable with other actors in the network. The question is how to find the right balance between them.

In order to truly compete with centralized platforms, **decentralized applications must provide user experience as good as or even better than what we are used to**. Iris and the other presented solutions are not quite there yet. Bittorrent does a great job with download speeds, but has no integrated content indexing and search like we’re used to on Netflix, Steam or Spotify. The others typically have performance or scalability issues. On the other hand, we can already boast offline-first capabilities and ease of signup unlike Facebook and the others. Not to mention the sheer ecstatic feeling of self-sovereignty.

![Iris logo](/assets/images/posts/iris-logo.png)

*Iris logo: rainbow colored eye in a speech bubble.*

If you’re enthusiastic about something that nobody else seems to get, odds are that you are chasing a rainbow (and Iris happens to be the Greek goddess of the rainbow). But sometimes you are right. In 2009 I emailed Satoshi Nakamoto and offered to help however I could with Bitcoin. After that it would take years before Bitcoin’s success eventually convinced people to start taking it seriously.

I have been similarly enthusiastic about the ideas behind Iris for years, but lacked the marketing skills to promote them. I believe that code speaks louder than words though: bitcoin wouldn’t have gotten off the ground with only the whitepaper and no reference implementation to prove it. Iris software is getting there, but progress is slow when you’re working on a complex system by yourself, using experimental building blocks that have changed many times along the way.

If you liked the analysis or the proposed solution, please share this article or check out [Iris on GitHub](https://github.com/irislib/iris/blob/master/README.md) for more contribution options. If you have a better idea on how to decentralize indexing or otherwise make us less dependent on corporate online platforms, please let us know. The world needs it!
