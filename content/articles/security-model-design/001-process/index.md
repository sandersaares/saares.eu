---
title: "Content security design, part 1 - the approval process"
date: 2019-05-09
draft: true
categories: "content security"
description: "How does one get approval to deliver Hollywood movies to users?"
---

Entertainment solutions are deployed in every part of the world, many of them showing high value content in high quality. What is necessary to get access to valuable movies? The solution author needs to prove to the studios that they will protect the content. Mostly this comes down to the following:

1. Only viewers with a right to view content can view it (e.g. considering geo-restrictions and similar).
1. The content can only be viewed using the solution in question, not exported or ripped for stand-alone playback.

The important constraints are both technical and contractual. A secure solution must provide assurance to the content owners that there exists a technical foundation that ensures the above points are fulfilled. This is achieved by defining a content security model that protects the interests of the content owners.

This is the first in a series of articles showcasing the technical design of such Hollywood-grade entertainment solutions, focusing on content security.

# Everything is relative

The level of security that a solution must achieve depends on the specific situation. Library content from a decade ago may often be usable without any meaningful protection, even in HD quality. The more recent the material and the higher its quality, the greater the demands placed on content security.

# The approval process

A content owner will review a solution's content security model and grant or withhold approval based on their internal rules. **There is no universal benchmark that determines whether approval is granted - the decision is always made on a case by case basis, taking into account not only the technical security mechanisms but also the business context**. The goal for the content owner is to balance the risk and reward of making the content available.

The content security model review is mostly based on documentation. The content owner will request detailed documentation and will often provide a content security questionnaire, asking for specific information of interest. Understand that this questionnaire is not a set of checkboxes to tick - it is there to supply information to a content security expert in a reasonably efficient and structured manner. Indeed, saying "no, we have no protection against this risk" is a perfectly valid answer to many of the questions.

The initial submission of documentation is often followed by deeper elaboration of specific areas of interest, helping the content owner's expert get a better idea of the situation. This will easily reveal any oversimplified or beautified descriptions of security-relevant processes that attempt to give an unrealistic impression of the level of security. Honesty and accuracy should be preferred in the content security model. The days when the reviewers did not understand content security are in the distant past and these days all content owners of any significance have actual security experts performing the reviews.

As a rule, there is no review of software or actual deployments - the content security model is evaluated on a documentation basis and any deviation from the documentation is (ideally) handled on a contractual level. Indeed, the software implementing the security model may sometimes not even fully exist at the moment the agreements with content owners are made. If the solution involves high risk physical systems (e.g. processing high resolution unencrypted content in some server rack) then an audit of the physical site security may be necessary.

After reviewing the security model, the content owner will make the decision on whether to approve access to their catalog and decide what level of access can be granted. If the content security model does not fully satisfy them, they may agree to grant a lower level of access than originally desired by the licensee - for example, only granting access to SD content. The decision is made based on business judgement and does not rely only on the technical factors. Certainly, a lucrative business opportunity can make the content owner take a more relaxed stance toward technical security.

If a higher level of access is desired by the licensee, a new review can be performed at a later date, after enhancing the security model. The content owner may point out areas that need improvement but as a rule, there will not be any direct conditions established. **The solution builder is expected to understand content security and to provide a comprehensive security model, not to tick checkboxes to achieve a higher level of access**.

The approval process needs to be performed individually with each and every content owner! Of course, having already gained approval from one studio can be a positive marker for the next studio, indicating that some level of industry trust has already been established.

# What is in a content security model

Everything relevant to content security should be described. The goal is to accurately describe all the work done to protect content from unwanted types of usage. An arbitrary and nonexhaustive selection of relevant topics might be:

* At which point is content encrypted and how? What prevents theft of content before encryption?
* How are the encryption keys created, associated with content and distributed throughout the system to components that need to access them? What are those components and why do they need access to content keys?
* How are encryption keys distributed to the devices performing playback and how is it ensured that only the right keys are distributed to the right devices?
* What industry-standard DRM systems and security mechanisms are applied to protect keys and content?
* What custom systems and security mechanisms are applied to protect keys and content?
* How are security updates distributed to system components? What process can be used for emergency patches if a zero-day attack is discovered and how fast is this process?
* What sort of human interaction is required for robust system operation? What aspects are automated?
* How does the system protect against insider attacks by malicious operators (if it does)?

Of course, the topics that are relevant for a specific solution will vary with each solution. The above is merely a useful starting point for consideration. The next few articles in this series will cover the basic principles that can be used to create a robust content security model.