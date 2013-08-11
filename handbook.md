This handbook is a work-in-progress. It's intended to be your companion for developing Substance applications. 

# Motivation

## Challenges of modern digital publishing

### Content Creation

In the beginning there is content creation. Text needs to be written, annotated and structured. Images, tables and lists need to be added. Today, the addition of interactive content (such as visualizations, interactive maps, etc.) is becoming increasingly important and should be supported by publishing systems. - See more at: http://blog.okfn.org/2013/01/15/content-as-data-towards-open-digital-publishing-with-substance/#sthash.PUUD5nOk.dpuf

### Quality Management

In order to ensure quality and consistency of digital content, publishers need to setup a peer-review workflow. Publishing systems must provide means for reviewers to suggest ideas and report errors, and should offer easy communication between reviewers and authors.

### Publishing

Once the content is complete, it’s time to share it with the public. Publishing used to be a manual process involving expert knowledge and consuming a substantial amount of time, but software tools have now automatized it. Authors should be able to share their work online themselves, without any manual steps being necessary.

### Change Management

Even if the best review processes were applied, all published content is prone to inconsistencies and errors. Over time, pieces of content need to be updated, additional information added, and new editions of the document published to ensure eventual consistency. Therefore publishing systems must support incremental updates, and offer an easy way to release new editions.


### Content distribution

Content distribution is becoming an increasingly complex issue today. Back in the day there was just paper, but today content is also consumed electronically on different platforms: on the web, Ebook Readers and Smartphones. And they are all different. There needs to be a smart mechanism that automagically turns one publication into a variety of formats (ePub, HTML, PDF) so as a publisher, you don’t have to prepare versions for each and every targeted platform.


## Possible Solutions

Over the last 2 years we have done a lot of research, and built a working prototype, Substance. Here are some of our conclusions about what makes a good digital publishing system.

### Separate content from presentation

Many traditional publishing systems store rich markup (such as HTML) and thus only allow publishing in that same format, which is a serious limitation when it comes to multi-platform publishing. How would you turn an HTML document into a printable version? How would you optimize it for Ebook Readers that use special document formats (e.g. Amazon Kindle)? By storing content (plain text) and annotations separately, it becomes possible for users to transform their documents into any format.

### Structured Composition

By considering a document as a sequence of content elements rather than one big chunk of formatted text, document editors can provide a better way of writing semantically structured content, as opposed to the visually optimized layouts offered by traditional word-processors.


### Offline Editing

We’ve seen the drawbacks of fully web-based publishing solutions, such as high latency and data loss. It turned out that providing an offline editor can significantly improve the user experience during editing and guarantee data security. Importantly information will stay private until users synchronize their publication with a public web-server. Moreover, authors can continue editing even if there’s no internet connection.


### Support for Collaboration

Authoring a publication is an iterative process that may involve many authors simultaneously editing a single document. During that process users should be enabled to add markers and comments to certain text fragments. Markers and comments should stay out of the user’s way, and only be shown contextually (e.g. when the text cursor is matching the corresponding marker).

### Extensibility

Editing requirements are fundamentally different among application domains. While book authors are comfortable with headings, text and images, scientists may demand more advanced content types such as formulas, data-tables and visualizations to prove their research findings. Publishing systems should feature a simple plugin system in order to allow user-specific content types.

# Substance

Substance is a content creation tool and a simple multi-format publishing platform. Whether you produce stories, books, documentations or scientific papers, Substance provides the tools that allow you to create, manage and share your content. It is being built with the idea of Open Knowledge in mind. So if you’d like to publish, comment on and collaborate around public documents, open access research or public domain texts, Substance may be for you.


## Open Source

Behind the scenes Substance is mainly composed by a stack of open source modules that are publicly released under the Open Source MIT license, so anyone can contribute and help developing an open standard for annotated text. Substance is meant to be an interoperable platform, rather than a product. Its infrastructure can be used by anyone to build specialized applications on top of it.

## Content is data

Substance considers content as data, which makes them accessible to computers and allows new ways of processing them. Documents can not only be viewed, they can be queried, just like a database. - See more at: http://blog.okfn.org/2013/01/15/content-as-data-towards-open-digital-publishing-with-substance/#sthash.tDsVpqDB.dpuf

## Semantic editing

Instead of editing a big canvas, Substance documents are composed of content elements. While existing solutions (like Google Docs) bring traditional word-processing to the web, Substance focuses on content, by leaving the layout part to the system, not the user. Because of the absence of formatting utilities, it suggests structured content-oriented writing.

## Custom Element Types

Substance.Article comes with a predefined set of element types. Out of the box you can choose from headings, text and images. However, it is easy to implement your very own document type and use it with your tailored version of the Substance Editor.

# Modules

## Substance.Data

Data.js is a data representation framework for Javascript. It's being developed in the context of Substance, an open publishing platform. With Substance.Data you can model your domain data using a simple graph-based object model that can be serialized to JSON. It's easy to manipulate and query data on the client (browser) or on the server (Node.js) by using exactly the same API.

### Usage

In your script

	var Data = require('substance-data');

Start with a schema.

    var schema = {
      "person": {
        "type": "person",
        "name": "Person",
        "properties": {
          "name": "string",
          "origin": "location"
        }
      },
      "location": {
        "type": "location",
        "name": "Location",
        "properties": {
          "name": "string",
          "citizens": ["array", "person"]
        }
      }
    };

Create a new `Data.Graph`.

    var graph = new Data.Graph(schema);
    

Add some objects.

    graph.create({
      id: "bart",
      type: "person",
      name: "Bart Simpson"
    });

    graph.set({
      id: "springfield",
      name: "Springfield",
      type: "location",
      citizens: ["bart"]
    });

Set properties.

	graph.set(["bart", "origin"], "springfield");


Querying is easy too. With `get` you can either look up a node by id or specify a path that is used to traverse the graph.

    // Return a node
    graph.get('bart');
    // => {
      id: "bart",
      type: "person",
      name: "Bart Simpson",
      "location": "springfield"
    }
    
    // Return a property
    graph.get(["springfield", "citizens"]);
    // => ["springfield"]
    
You can even do smart querying and have the correct objects returned instead of ids.

    // Return a property
    graph.query(["springfield", "citizens"]);
    // => [{id: "springfield", type: "location", citizens: ["bart"]}]


### API

API docs are not yet ready. However to get an overview of the full API please have a look at our commented [testsuite](https://github.com/substance/data/tree/master/tests).

## Substance Document

Substance Document is an open standard for manipulating structured digital documents. It helps with the *creation* and *transformation* of digital documents. It ensures *consistency*, separates *content* from *presentation* and provides an easy to use API. It depicts the heart of the Substance platform, a set of tools for content creation and distribution.

A Substance Document can range from loosly structured content involving headings and text, such as reports or articles to more complex things that you wouldn’t consider a traditional document anymore. The format is designed to be extensible, so you can create your own flavors of documents. We put a lot of thought into the design of this module. This release of Substance.Document is a result of more than 12 months of research and development, so we are looking forward to your feedback.

<!-- 
### Play with the Console

Without too much talking, just have a look yourself. The Substance Console allows you to explore some examples and to mess around with the document manipulation protocol in a playful manner.

<iframe width="800" height="600" frameborder="0" scrolling="no" src="http://interior.substance.io/document/">
</iframe>-->


### Design goals

- A document consists of a sequence of content nodes of different types (e.g. heading, text, image)
- A document is manipulated through atomic **operations**
- The **history** is tracked, so users reconstruct previous document states at any time
- Support for incremental text updates, using a protocol similar to [Google Wave](http://www.waveprotocol.org/whitepapers/operational-transform)
- Support for text **annotations** that are not part of the content, but rather an overlay
- Support for **comments** to have dicussions that can stick on content elements or annotations.


### Getting started

This section is intended to be a step to step guide on how to use the module to programmatically create and transform digital documents of any kind.

**Start tracking a new document.**

    var doc = new Substance.Document({ id: "my_doc" });

**Add a first heading to the document.**

	var opA = ["create", {
        "id": "h1",
        "type": "heading",
        "content": "Heading 1"
      }
    ];

    doc.apply(opA);

**Now let's add another node, this time a text node.**

This operation is pretty similar to the previous one, except this time we specify `text` as the content type.

	var opB = ["create", {
        "id": "t1",
        "type": "text",
        "content": "Text 1"
      }
    ];

    doc.apply(opB);

**Position nodes**
	
    var opC = [
      "position", "content", {"nodes": ["h1", "t1"], "target": 0}
    ];
    doc.apply(opC);
    
    doc.getState();

**Update an existing node**

There's a special API for incrementally updating existing nodes. This works by specifying a delta operation describing only what's changed in the text.

    var opD = [
      "update", "h1", "content", [4, "ING", -3]
    ];

    doc.apply(opD);
    doc.get('h1').content; // => "HeadING 1"

**Inspect the document state**

Now after executing a bunch of operations, it is a good time to inspect the current state of the document.

    doc.toJSON();
    
This is how the JSON serialization looks like:

    {
      "id": "my_document",
      "nodes": {
        "document": {
          "title": "",
          "views": ["content"]
        },
        "h1": {
          "content": "HeadING 1",
          "id": "h1",
          "type": "heading"
        },
        "t1": {
          "content": "Hey there.",
          "id": "t1",
          "type": "text"
        },
        "content": {
          "nodes": ["h1", "t1"]
        }
      }
    }

As you can see there are two nodes registered, which can be directly accessed by their `id`. In order to reflect the order of our nodes we keep a view node `content` that has a `nodes` property reflecting the node order in the document.

### Versioning

This is where things are getting exciting. Substance.Document has first-class support for versioning through [Substance.Chronicle](http://interior.substance.io/modules/chronicle.html). So if you instantiate your document with a chronicle attached, you can do time travels.

    var versionedDoc = new Substance.Document({
      chronicle: Chronicle.create()
    });

From now on, all the applies are recorded.

    versionedDoc.apply(opA);
    versionedDoc.apply(opB);
    versionedDoc.apply(opC);

Now you can magically navigate the document's history, e.g. a simple undo.

    doc.chronicle.rewind();

You can also checkout a particular version by

    doc.chronicle.open(sha);


### Annotations

So far, we have a bare-metal digital document, containing two different types of content nodes. Now we'd also like to store additional contextual information, relevant to a particular portion of text within the document.

Unlike in other systems with Substance annotations are not part of the content itself. They're completely separated from the text. Most text editors offer the ability to emphasize portions of text using markup. E.g. in HTML it looks like this.

    <em>Emphasized term</em> in a text body.

In Substance however, we keep annotations external and remember the position of the first character, as well as an offset (how many characters are effected). An annotation emphasizing the "Hey" in "Hey there." looks like so:


### Insert annotation

Like document content, annotations are manipulated through operations.


    var op = ["annotate", "content", {
        "id": "a1",
        "type": "emphasis",
        "range": {start: [0,1], end: [0, 5]}
      }
    ];
    
    document.apply(op);

### Comments

Substance has in mind the usecase of collaborative composition of documents. Thus it allows a lively discussion during the editing process.

So if you wanted to support comments in your document model, you can can just define a new annotation type `comment` and stick it on either a content node or reference an annotation.

To learn about the full API, please consult our [test suite](https://github.com/substance/document/blob/master/tests). It should be easy to follow the examples.

