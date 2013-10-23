<!-- First, the focus on the importance of a paper in the publishing decision often deemphasizes technical issues.And, more importantly, the current system relies on three reviewers judging the technical merits of a paper under a fairly strict time constraint – conditions that are not ideally suited to recognize anything but the most obvious flaws. In my experience the most important technical flaws are uncovered after papers are published. And yet, because we have a system that places so much emphasis on where a paper is published, we have no effective way to annotate previously published papers that turn out to be wrong: once a Nature paper, always a Nature paper."

http://www.michaeleisen.org/blog/?p=694#sthash.2c6rFxUB.dpuf
-->


<!-- See: http://www.michaeleisen.org/blog/?p=1439 -->

<!-- http://oaopenaccess.wordpress.com/2013/10/09/truthiness-isnt-quite-truth-and-sciencey-isnt-quite-science-even-if-published-in-science-mike-taylors-anti-tutorial-how-to-design-and-execute-a-really-bad-study/ -->

<!-- **Scenario** good idea?
- paper gets published
- readers download pdf version
- reader take notes either on paper or using Adobe Acrobat
- author's can't be contacted easily
-->

<!-- Title: Substance Annotator -->

Vision
=====================================================================

Content providers across all domains (scientific publishing, news, education, books) are facing the very same challenges when it comes to implementing an effective digital publishing workflow.
From receiving a manuscript to peer review to publishing many manual steps are necessary. Communication usually happens offline (via email etc.) which is not only costly and time-consuming but also error-prone and intransparent.



An ultimate goal would be to create a fully integrated, interactive environment that

- close the gap between authors and publishers,
- make it easier for authors to create publications,
- exploits web-browser technology to improve the reading experience,
- allow social interaction to make working with publications more lively,
- optimize publishing workflows by exploiting a better document exchange format
- improve peer-reviewing processes by adopting integrated annotations and comments
- TODO: more

From our experience we think that pursuing these goals all at once is not realistic.
Publishers are in a strong business competition with other publishers
and are not taking a greater financial risk to replace their established workflows.
On the other hand, authors typically are used to certain text-editing tools
and prefer to stick their tool chains as long there is no real extra benefit.

Therefore, we see the need for a pragmatic strategy to pursue a partial solution
that should increase the acceptance on both sides
by bringing instant benefit for authors and publishers.
At the same time such a solution would prepare the environment and would pave
the way for a fully integrated solution for Open Digital Publishing.


Goals
=====================================================================

<!--
TODO:
- describe goals of this application
- why are they reasonable? what benefit?
-->

An interactive workspace for reading and discussing scientific articles...

- Browser-based reader which is providing an improved reading experience,
  superior to conventional approaches (e.g., PDF documents)
    - increases popularity of working with digital publications
    - increases the acceptance on the side of readers (scientists)
    - encourages publishers to switch to an improved document input format
      which can be processed by Web-browsers
- Annotations and Comments:
    - provides new functionality to stand out from conventional document readers
    - encourages communication and collaboration between authors and scientists
    - provides a solution that can be applied to the review-process
      preparing future improvements for
- Reader made available for Mobile (Tablets)

Why and how could an integrated system for Annotations/Comments improve the situation?

- Articles are mostly printed out and read on paper
- Notes are usually taken offline, there's no easy way to share comments yet
- Current online commenting systems do not permit per word/letter comments
- simplify the reviewing process:
     - editors and reviewers would be provided with a reader
     - reviewers would be able to leave comments in-place
     - editors could evaluate reviewers comments in a more appealing
- communicate about published work:
     - other authors could profit of a system for leaving notes for personal use
     - other authors could contribute to a discussion or provide corrections
     - for corrections, editors could be provided with material (from discussions)
       to initiate
- increase popularity of publisher sites
- encourage a more lively interaction with published documents

This tool is built on top of the [Substance](http://substance.io) technology stack and has been successfully integrated by [eLife](http://elife.elifesciences.org) and [Landes Bioscience](http://landesbioscience.org).

## Annotation and comments as part of the reading experience

We would like to create a reading experience that takes full advantage of the opportunities offered by digital media.
While there are existing solutions for annotating web-content, they aren't yet frequently used, mostly because of usability and integration issues.
There's consensus that for optimal usage, commenting systems need to be integrated tightly with the reading experience.
We'd like to utilize our experience from building Substance and eLife Lens and implement a functioning prototype within 6 months. With further financial support from publishers we'd like to help them integrating our system into their journal websites.

![](http://f.cl.ly/items/1g2G1N2a1g3s462v0V09/substance-annotator.png)

## Collaborative examination of content

In research papers many technical flaws are uncovered after papers are published ([Michael Eisen](http://www.michaeleisen.org/blog/?p=694#sthash.2c6rFxUB.dpuf)). By providing an easy way to express thoughts on particular content areas, we would like to implement a culture of collaborative examination of content. Research papers should no longer be dusty static pieces, they should turn into lively discussions. Once that happens it could be the beginning of **post-publishing peer-review system**.

<!--
*Scenario?*
-->

<!--
- extended peer review (iterative)
  - editors and authors
  - readers (post publishing peer review method)
-
-->


<!-- - it's easier to understand the authors arguments, if readers have a platform for asking questions / starting discussions -->

## Redefining impact

The importance of a paper is usually determined by the impact factor of a journal, and additionally how often the paper has been cited in other papers. Now if we had a working annotation/commenting system, we could introduce a new metric determining importance.

## Peer-review

Publishers can easily integrate the proposed comment system into their peer review processes. That way editors have a much more effient way for communication.

<!-- - We provide an oline reading experience that's better than paper-->

Execution
=====================================================================

1. Describe the current state:
    - Reader: based on elife lens
    - Document Model (including Annotations): Substance.Document, Substance.Article
    - Platform for User-Annotations: Hypothes.is
2. What will be done? and how?
    - User interface! annotation/commenting system that works on published NLM articles
    - Define an interface to Hypothes.is for storage
    - Integration into extisting journals (eLife, Landes,...)
3. Time schedule / Roadmap


We would not have to start from scratch. We can already rely on a solid technical foundation.

## Background

In 2013 Ivan Grubisic and Michael Aufreiter have developed an interactive reading interface for scientific content, [eLife Lens](http://lens.substance.io).
![](http://cl.ly/image/100N0l3G2V2Q/cid%3A6C28E9D0-3D4E-4270-9FA2-9DF2250839B1.png)


## Substance

![](http://backbonejs.org/docs/images/lens.jpg)

This tool is built on top of the [Substance](http://substance.io) technology stack and has been successfully integrated by [eLife](http://elife.elifesciences.org) and [Landes Bioscience](http://landesbioscience.org).

We received overall positive feedback from the scientific community, when launching Lens. However, we would like to take our ideas further, by creating an new interface that has support for annotations and comments built in.

## Substance

- We're the team behind Substance.io
- What is Substance

## eLife Lens

Together with graduate student Ivan Grubisic we developed eLife Lens, which serves. We'd like to thank eLife for funding this important ground work!

### Hypothes.is

We're partnering with Hypothes.is which will be responsible for storing annotations and comments in their system.

<!--## Unique selling points
### Data Model
### Open Source
-->

By encouraging authors and publishers to use and evolve open software components and a lightweight exchange format usable by web-clients, we reduce the obstacles that originate from economic competition and pave the way to true open publishing and an Open Science Information Knowledgebase.



# Outlook

Referring to the initially described vision, describe the impact of this work.
- what next steps are possible?
- what would be need to be done?


Voices
=====================================================================

- Ian Mulvany
- Dan Whaley
- Randy Schekman

```
Add your voice: Send us an email to info@substance.io.
```
