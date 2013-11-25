It's about time for an update on the state of Substance development. Earlier this year we were awarded with the [Shuttleworth Flash Grant](#blog/shuttleworth-grant).

![](http://f.cl.ly/items/3b1G0i0t0O452C0b0c30/shuttleworth-1.jpg)

It allowed us to invest more dedicated time into modularization and making our [core API's](#blog/substance-io-relaunches) stable. 

# Evolving our Mission

It's been three years since I started Substance as an effort to build a semantic editing environment for the browser. Since then the idea evolved and I realized that the concept of strictly separating *content* from *presentation* could have a huge impact in many fields where digital content plays an important role (science, education, journalism, open government, etc.).

With Substance we want to realize broader acceptance of *digital content* in general. By deeply integrating *annotations* and *comments* into authoring and reading environments we want to implement a natural way of human collaboration that is supported, not dictated, by software. There are not only technical aspects (consistency, versioning, replication) that require our attention. We want to complement our low-level technology stack with a set of carefully crafted highly functional user interface components for editing and contribution management.

After all, Substance is being designed to be integrated into existing systems, with an emphasis on easy customization. We want to help others to make [open annotation](http://hypothes.is/), [open text books](http://www.shuttleworthfoundation.org/fellows/mark-horner/), open government etc. a reality faster.


# Where are we at?

Here's a quick run-down on what we've accomplished in the past months. I'd like to thank again Mark Horner and the [Shuttleworth Foundation](http://www.shuttleworthfoundation.org/) for their support.

## Interactive Reading

The web browser provides a unified platform for viewing content. Instead of binding the content to a presentation-focused format, Substance considers content as data paving the way for a new generation of tools. Using this approach, we built [eLife Lens](http://lens.substance.io) an interactive viewer for scientific literature, which has been welcomed by the academic cummunity.

Based on that work, we extracted the [Substance Reader](http://github.com/substance/reader) module, which can be used to display any Substance-based article. The reader is designed to support desktops (2-panel view) and mobile devices (details on demand). Customization is possible without touching the codebase. For instance, if you wanted to display interactive visualizations along with your content, you'd have to configure a custom article format. Since the Substance Reader implements a defined interface, it can display different article types at the same time. You can learn how to use the Substance Reader by taking the [Substance Tutorial](#substance/tutorial).

## Browser-based document manipulation

With the [Substance Document Model](http://substance.io/#substance/manual/toc/header_6) we developed an open framework for manipulating structured digital documents in the browser. It is designed to ensure *consistency*, stricly separates *content* from *presentation* and provides an easy to use API. This abstract model serves as an interface for custom document models, that can be defined by domain experts. The Substance Document Model is unique in that it doesn't require any server side infrastructure, which makes it really easy to integrate into exisiting systems. Using the provided API users can create content elements and *annotate* them in various ways. We also have implemented support for [incremental changes](http://substance.io/#substance/manual/toc/header_13) and [versioning](http://substance.io/#substance/manual/toc/header_15), which is crucial for implementing *collaborative workflows*.

Substance Document makes developing web-based viewers and editors much easier, by providing the first web-native document model. This model operates on a JSON data-structure rather than HTML, allowing the user to query the document like a database.

<!-- ![](http://f.cl.ly/items/2I3J3X2z3M3918151w0G/explore.png) -->

## The Substance Article

The Substance Article serves as a reference implementation for Substance-based document formats. In the current version, there is support for most common content types, such as paragraphs, headings, images, lists and tables. It provides a document manipulation API for Javascript as well as view compontents and default styles, individually for each content type. With [Substance Nodes](http://github.com/substance/nodes) we are a providing a common set of reusable content types, which can be easily adapted by users.

One example is the [Lens Document Format](http://lens.substance.io/#lens/lens_article), which adds support for domain specific content, such as rich figures, citations and supplemental materials.

## Import / Export

The Substance Converter lets you turn existing content into a Substance Article. You can import from Markdown, Media Wiki, ODT and many others. Of course this also works the other way around. Learn how to convert and display your existing Markdown content in our [tutorial](#substance/tutorial).

# What's next?

<!-- We do have a lot of plans for the future. -->

## Substance as a business

Together with [Oliver Buchtala](http://github.com/oliver----), a very good friend of mine, we'll be starting the Substance Software GmbH with the beginning of the new year. We'll offer consulting in the context of digital publishing, and in the long run commercial licenses for higher level open source modules and products.

Behind this formation is our dedication to work on Substance full-time. We'll keep the open source spirit but also ensure that our work is backed by a sustainable business model.

## The Substance Composer

Now that we have a set of reliable building blocks we're switching back gears to developing our full-fledged editing solution. The **Substance Composer** will ship as a native application for all major OS in a fully functional beta version in summer 2014.

![](http://f.cl.ly/items/3H2l2h3B0Y273S2e2M2V/Screen%20Shot%202013-11-25%20at%2017.29.24.png)

Here's a sneak peak on the new minimal editor we just started building. The interface is influenced by our work on [eLife Lens](http://lens.substance.io). Essentially, we want to turn a proven reading environment into a writing space, that doesn't stand in your way. We're excited for the coming months and I hope you are too!
