Today we relaunch Substance.io as an effort to put more emphasis on Substance as a platform. With Substance, we would like to contribute an extensive **content creation** and **annotation** framework built on **web** infrastructure. It is designed to be customized and integrated into existing workflows.

## Substance 0.5.0

Along with the relaunch of Substance.io we release the version 0.5.0 of the Substance stack. 0.5.0 ships with the following modules.

- [Substance.Data](http://github.com/substance/document) - A data representation framework for Javascript.
- [Substance.Document](http://github.com/substance/document) - A JSON-based document model, that can be customized
- [Substance.Article](http://github.com/substance/article) - Reference implementation
- [Substance.Operator](http://github.com/substance/operator) - Support for incremental changes using Operational Transformation
- [Substance.Chronicle](http://github.com/substance/chronicle) A git-inspired versioning API optimized for digital content
- [Substance.Surface](http://github.com/substance/surface) - A building block for displaying and editing documents
- [Substance.Nodes](http://github.com/substance/nodes) - Common node type implementations such as `Paragraph`, `Heading`, `Image`.

Please have a look at the official [Manual](#substance/manual) to learn more about the individual modules. For a general introduction see [here](#about).

Limitations

We're still owing you a stable rich text editor. We've got really far, but the editor is not yet stable enough to be part of the release.


## Substance IO

The new Substance.io is powered by our new minimal publishing system, [IO](http://github.com/substance.io). It lets you write your article in Markdown and define figures, tables etc. in a simple JSON syntax. All that input is compiled into a full-fledged Substance Article including the main content, meta information like the title and authors and figures you have specified. It works similarly to Jekyll, a static site generator written in Ruby. Compiled IO document repositories can be hosted on any webserver. It's only a bunch of static files.

## Substance in the wild

A platform is only a platform if applications built on top of it. We are happy that there's a production-ready Substance app out there. And there are more to come.

### eLife Lens

![](http://f.cl.ly/items/3P013m1y270K0D0J0L3W/Image%202013.10.16%201%3A02%3A27%20AM.jpeg)

In collaboration with Open Access publisher eLife we developed a new way to display scientific content, [eLife Lens](http://lens.substance.io). This tool is built on top of the Substance technology stack and has been successfully integrated by [eLife](http://lens.elifesciences.org/00311/) and  [Landes Bioscience](http://landesbioscience.com).

### Fidus Writer

We're teaming up with the guys behind [Fidus Writer](http://fiduswriter.org/). They already have a working solution for editing scientific documents in the browser. Together we'll be building version 2.0, using the Substance technology stack, allowing incremental updates, versioning and replication for collaborative workflows. 