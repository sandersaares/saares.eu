---
title: "DRM in HTML: what EME has and has not done for us"
date: 2017-07-14
categories: ["content security", "standards"]
description: "How Encrypted Media Extensions changed the industry and what happens next."
---

The World Wide Web Consortium has recently made a decision to publish Encrypted Media Extensions (EME) as a web standard. [This has drawn criticism from many directions](https://arstechnica.com/information-technology/2017/07/over-many-objections-w3c-approves-drm-for-html5/) because EME standardizes a mechanism that is highly opaque to users, has the potential to jeopardize their privacy and brings considerable legal risk to any researchers that try to study it.

Despite this, EME is a step up in interoperability and has incorporated basic privacy-oriented features that were lacking in pre-EME technologies. To better understand what EME truly brings to users, one needs to understand not only what it is but also where it comes from and what future directions it and related technologies may take.

# What exactly are DRM and EME?

Studios that license premium content require video solutions to use Digital Rights Management systems (DRM) that enforce strict control over what users can do with the content. Premium content is delivered to users in encrypted form, ensuring that even if the data is intercepted and copied, it cannot be played back without the required key. Each player must cooperate with a DRM system — a component of the user’s device — that is tasked with obtaining and protecting this key and ensuring that the decrypted content can only be displayed for immediate viewing and not copied.

{{< figure src="EME - API.png" title="EME defines an API and various data structures, often used merely to wrap DRM system specific data." >}}

[EME is an API that defines standard functions and data structures](https://www.w3.org/TR/encrypted-media/) that can be called form JavaScript in order to activate the DRM system used by the browser and to supply it with data. It does not standardize how DRM systems protect content or keys, or even how they obtain those keys and allow them to be used. Most of the actual messaging involved remains DRM system specific and is simply wrapped by EME data structures. EME provides an on-switch and a feedback mechanism to allow the DRM system to inform the web page about the presence or absence of keys.
DRM in the world before EME

The concept of DRM has been around for decades, gaining significant uptake in the 80s and 90s in cable and satellite television and then spreading to personal devices like the iPod and Zune. It is from here that it made the leap to the web browser when Microsoft published the Silverlight 2.0 plugin in 2008, [taking Zune’s PlayReady DRM technology along for the ride](https://msdn.microsoft.com/fr-fr/library/cc838192%28v=vs.95%29.aspx). Silverlight was promoted heavily and reached an installed base of around 70% in a few years.

As Silverlight was available not only for Internet Explorer but also for other browsers and even on Mac OS, it presented a very attractive target for solution developers who wanted to offer their customers the ability to play back premium content. Companies like Netflix were quick to take advantage of this capability. Suddenly, even small independent solutions could ensure that playback was protected and thereby license content from serious movie studios.

Other companies quickly piled on to take a bite of this fast developing market opened by Microsoft, with Flash integrating DRM support and various other vendors offering their own browser plugins for DRM-enabled playback. Their approaches to business were quite different and video playback technologies were at the same time evolving in other ways that lead to a slow uptake of alternative DRM systems, causing Microsoft to come out more or less on top of the browser DRM game. Still, the era of browser plugins was ending and Silverlight usage quickly declined as HTML 5 made the web more unified and presented a convenient alternative to plugin-based rich web app development. Yet for a long time there was no serious alternative for DRM and video playback remained a plugin-driven activity far into the HTML 5 age.

In hindsight, we can say that browser plugins were a particularly buggy phenomenon — think of [the endless security vulnerabilities of Flash](https://www.cvedetails.com/vulnerability-list/vendor_id-53/product_id-6761/Adobe-Flash-Player.html). The concept of regularly updating browser plugins never really reached the majority of users who as a result were often using outdated software. Furthermore, plugins were completely opaque to the users — a plugin was a black box, providing whatever functionality its authors decided to include. There was nobody advocating for the rights of users in this arrangement — you had to click the install button and accept whatever came or you had to move on and not consume content on your desired website.

The system worked despite its flaws and it was the best that the industry could provide in its day. However, plugins endangered users’ computers and caused frustration for solution developers who had to not only convince users to install buggy plugins but then also had to support those users when they inevitably ran into issues. As competing DRM technology stacks were completely incompatible with each other and no single one covered all platforms and device types, ambitious solution developers often had to set up multiple parallel content delivery flows to serve a wide range of platforms, making it expensive to offer premium content to a wide range of users.

# How EME was born

In the early 2010’s it quickly became apparent to many in the industry that with the decline of browser plugins an alternative was needed to ensure that premium content could still be provided to users. If there is no plugin the only thing left is the browser. Yet before tackling the hard topic of DRM, another needed attention. Not only were the browser plugins responsible for DRM but also the actual playback of content, using modern adaptive streaming technologies that could adjust the playback experience according to the the user’s internet connection capabilities. This could not be done by the browsers, which were only capable of playing back simple MP4 files, if that.

The first technology to be standardized was Media Source Extensions which defined [a mechanism for the web page to directly feed content to the browser’s media engine](https://www.w3.org/TR/media-source/). The browser took on the complexity of decoding and rendering media and of making use of the device’s hardware acceleration features, none of which could be feasibly done by the JavaScript code running in a web page. This was largely uncontroversial and opened the door to begin standardization of DRM related features along similar lines.

As work on Encrypted Media Extensions started it quickly became apparent to many observers that not all participants really understood DRM. This caused significant friction and never truly went away, with different parties approaching the topic from very different viewpoints and some harboring rather unfortunate misunderstandings of what exactly was being worked on. User privacy has been a topic raised time and time again, yet companies implementing EME are often happy with the status quo as they have a conflict of interest in maintaining their DRM technologies that often rely on obfuscation and secrecy to provide security. Firefox developers have stood out at times by speaking up about the rights of users in the W3C working group. Unfortunately, the very same Firefox developers have often been relatively uninformed about the DRM market, making their efforts ineffective.

Web standards are usually developed in parallel with implementations and EME was no different. Two major browser manufacturers — Microsoft and Google — each had their own DRM technology and they were eager to get it on the market in a widely usable form. While discussions were ongoing, their browsers implemented what seemed to be the most sensible opinion of the day and sometimes created custom API extensions where there was no EME-provided solution. There came a point in the EME standardization process where the two major browser families had working DRM implementations accessible by EME with the core features implemented in a way essentially compatible with EME. Motivation to continue the standardization quickly declined and for a long time around 2015–2016 EME standardization became something of a purely theoretical exercise, with implementations already in active use in forms resembling various drafts of EME.

Things never really changed after that — the more advanced features were dropped from EME due to lack of implementations (required for standardization). Browser authors did not see the point in implementing more EME features as solution developers appeared quite happy to make do with what was already there. In the final stretch of standardization, there has been a slow trickle of convergence but the possibility for EME to drive browser feature development in the field of DRM is largely gone. I suspect this is one of the main reasons why W3C is going ahead with standardization — EME in practice has been a done deal for a year or two already. It is in widespread use and blocking standardization will not get rid of EME or change what browsers do. In many ways, EME survives at the mercy of browsers, not the other way around.

# Opening the market for competition

Behind the scenes, Netflix was the major driving force that motivated platform developers to incorporate readily available media technologies into their browsers and consumer devices. The wave of standardization was largely driven by their massive success in online video. The content pieline — processing, delivery, playback and protection — has always been a massive cost center for solution developers and the lack of standardization often forced companies (that could afford it) to maintain multiple parallel workflows to serve different platforms utilizing different technologies. Platforms that supported standard mechanisms could get a Netflix presence very easily, thereby motivating smaller platforms by enabling them to offer familiar services to users and larger platforms by creating competition.

While some browsers are created by companies who are also DRM technology developers, others are not. One thing that EME standardizes is the ability for the web page to choose a DRM system from multiple options presented by the browser. This enabled Firefox to create some welcome competition in the DRM market, dominated by software giants Microsoft and Google, when Firefox chose to integrate Adobe’s DRM technology. As it turned out, Adobe never succeeded with DRM due to their sales approach that consisted of only going for the largest customers. A few years down the line, Google stepped in to integrate their Widevine DRM technology into Firefox, as an option more accessible to solution developers. Thus the availability of premium content for Firefox users was greatly increased, enabling the browser to remain competitive. At the same time, choices in DRM systems were again reduced by the lack of Adobe’s commercial success in the field of DRM.

Some platforms such as [Chromecast and many Android devices incorporate multiple DRM technologies out of the box](https://developers.google.com/cast/docs/media#delivery-methods-and-adaptive-streaming-protocols) and expose them using EME or [an equivalent non-browser technology](https://developer.android.com/reference/android/drm/package-summary.html), enabling not only competition between browsers and platforms but also between different DRM technology providers. Five years ago, each DRM technology provider took a royalty payment whenever their technology was used to deliver a decryption key. Today, all major DRM technologies are royalty-free in this regard — largely due to the competition encouraged by the wide uptake EME.

# Future opportunities

DRM systems remain opaque to users — while EME standardizes the mechanism of activating them, it does not affect what DRM systems actually do. Users have little to no control or visibility over the information collected by DRM systems or the rights that are assigned to them. DRM remains a boolean factor that simply determines whether a video plays back or does not. Any information exposed to the user comes from the website they use, which often says nothing about DRM. Indeed, the user may not even be aware that there is a component in his device that is actively working to protect data from the device’s owner.

Increased competition in the field of DRM system development is the best hope for achieving more results in this area. If users are able to select the DRM technologies they wish to use, competition may force DRM system authors to accept privacy-oriented standardization. EME opens the door for choice between DRM technologies, though few platforms actually enable a choice to be made as most only implement a single DRM technology.

Even when there is a choice of DRM technologies, the decision is made by the solution developer, based on what technology is preferred by them. This is largely driven by technological needs — remember that EME only standardizes the mechanism of DRM system activation. There is nothing even remotely standardized about key management workflows and digital rights policy application. These are closely guarded secrets of DRM technology authors. While differentiation between DRM systems cannot and should not be avoided — it is the differences in technologies that drive competition, after all — this secrecy about the related proprietary formats for key delivery and policy control is mostly meaningless and simply driven by inertia and lack of a reason to do it any different. 99% of the currently-secret communication protocols and formats could be opened for standardization without and loss of security in terms of content protection.

It is here that the needs of solution developers overlap with the needs of users — for developers, having to work with different DRM technologies causes needless duplication. Many companies with DRM experience create their own generic abstractions over DRM technologies that enable their solutions to work with them all using a single unified interface. From here, there is only a short leap toward true standardization of DRM protocols. This topic has been raised both in W3C and in private industry forums several times but in every instance the drive to act dissipates as it quickly becomes clear to us that nobody with enough pull in the industry (i.e. the DRM technology providers) would actually implement any of it.

A lack of motivation to implement standards is the major factor we need to overcome if we are to open up DRM for the world. Competition is what forces companies to act and EME has done a good job of bringing a small bit of competition to the web by enabling different parties to make use of DRM with reduced development effort. It is by increasing this competition in new ways that we can drive further actions. Writing standards motivated by noble goals of interoperability or the protection of user rights is not enough — companies need to to put their money behind implementing the standards and that will only happen if they have something to gain from it. In the end, DRM is a mechanism that enables solution providers to attract more users by enabling premium content playback and this is the lever that can move the industry.