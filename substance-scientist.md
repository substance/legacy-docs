# Describe your project in one sentence

By integrating Substance Scientist into your workflow, authors, reviewers, publishers and typesetters can collaborate on a document using a single source of information throughout the whole lifecycle.

# Project description

There's large consensus that traditional publishing processes are costly, inefficient and prone to errors. With Substance.Scientist, we'd like to provide a web-based editor that sits right at the beginning of the publishing workflow - at the content creation stage.

There's no writing environment that outputs semantically rich, machine-processable data. We believe that is really the root of the problems most publishers are facing. We believe that an an annotated web of scientific literature can only exist when annotations are made in the content creation phase.

We're aware that our small team won't be able to come up with a full stack solution for submission, peer-review and publishing, including all the infrastructure needed to operate the service. Instead we'd like to focus on one of the core problems that haven't been solved yet - content creation. Content authors and publishers will be able to easily integrate the editor into their submission, review and publishing processes. They'll save time and costs and be able to focus on their work as scientists. We'd consider ourselves as software-compontent provider, rather than a service provider.


# Motivation

## Weaknesses of traditional publishing workflows

Open Access publishers rely on the JATS (formerly NLM) XML document format. NLM has been designed primarily for supporting a print-workflow. It isn't well-suited for digital publishing workflows, simply because it lacks structured information. The specification allows content to be free-form in most places. Reasoning on the data is hard and time consuming, if possible.

## Reducing manual work

In reality manuscripts are sent as static files (e.g. MS Word). A lot of manual work is needed to turn them into the JATS format, which is used during review. Typesetters can only operate at high costs, since they manually have to make tweaks to the source XML file, while they should actually be able to focus on layouting.

## Change management

All content is prone to inconsistencies and errors. Especially during the review process, pieces of content need to be updated, leading to new versions of the document. Thus, modern publishing environments must support incremental updates and versioning. This not only refers to the main content of the document, but also to annotations which need to co-transformed when changes are made.

# Goals

## Separate content from presentation

Many traditional publishing systems store rich markup (such as HTML or XML) and thus only allow publishing in that same format, which is a serious limitation when it comes to multi-platform publishing. How would you turn such a document into a printable version? How would you optimize it for Ebook Readers that use special document formats (e.g. Amazon Kindle)? By storing content (plain text) and annotations separately, it becomes possible for users to transform their documents into any format.

## Content is data

Substance considers content as data, which makes it accessible to computers and allows new ways of processing it. Documents can not only be viewed, they can be queried, just like a database.


## Semantic editing

Instead of editing a big canvas, Substance documents are composed of content elements rather than one big chunk of formatted text. While many existing solutions (like Google Docs) bring traditional word-processing to the web, Substance focuses on content, by leaving the layout part to the system, not the user. Because of the absence of formatting utilities, it suggests structured content-oriented writing.

## Offline Editing

We’ve seen the drawbacks of fully web-based publishing solutions, such as high latency and data loss. It turned out that providing an offline editor can significantly improve the user experience during editing and guarantee data security. Importantly information will stay private until users synchronize their publication with a public web-server. Moreover, authors can continue editing even if there’s no internet connection.

## Support for Collaboration

Authoring a publication is an iterative process that may involve many authors simultaneously editing a single document. During that process users should be enabled to add markers and comments to certain text fragments. Markers and comments should stay out of the user’s way, and only be shown contextually (e.g. when the text cursor is matching the corresponding marker).


## Extensibility

Editing requirements are fundamentally different among application domains. Substance.Scientist ships with a predefined set of element types. Out of the box you can choose from headings, text, figures and citations. However, it is easy to implement your own element types, and use it with your tailored version.

## Open Source

Behind the scenes Substance is mainly composed by a stack of open source modules that are publicly released under the Open Source MIT license, so anyone can contribute and help developing an open standard for annotated text. Substance is meant to be an interoperable platform, rather than a product. Its infrastructure can be used by anyone to build specialized applications on top of it.

# Roadmap

We'd like to follow an iterative approach with deliverables about every 3 months. We'd like to run user tests after completion of each stage and start early integration experiments to make sure we don't miss use-cases of end users.

- 1st stage (Q1 2014) - a stand-alone experimental editor for paper submission ready for user testing
- 2nd stage (Q2 2014) - Ready-to-use (still experimental) client, that allows authors to make a submission that can be exported to an NLM file (which can be integrated into existing publishing worfklows)
- 3rd stage (Q3 2014) - peer review features (support for annotations, comments, everyone can see the current state of the evolving doc)
- 4th stage (Q4 2014) - Basic publishing workflow integration (e.g. one click submission) but main focus is on shipping a solid/polished version of the editor.

# Related work

We are the team behind [eLife Lens](http://lens.elifesciences.org), a new display method for scientific literature and [Substance](http://substance.io), a web-based publishing environment that is being developed since 2010. We've learned a lot of lessons in the past years and we'd like to bring in our expertise and help replacing legacy publishing workflows with modern ones, step by step.


