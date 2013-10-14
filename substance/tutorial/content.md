Welcome to the Substance Tutorial. You'll learn:

1. How to [convert](convert) a Markdown file into a Substance Article
2. [Display](display) Substance content in our interactive reader.
3. Create a customized [renderer](renderer)

*The tutorial is at an early stage. We'd like to improve it over time and always keep it up to date with our latest API's. You can help us making this tutorial better by contributing to the source [Markdown file](https://github.com/substance/docs/blob/0.1.x/substance/tutorial/content.md) and also to the [example code](http://github.com/substance/tutorial).*


Preparations
=====================================================

Make sure you have the following software packages installed on your computer before starting over with the tutorial.

   - [Node.js](http://nodejs.org/) >=0.10.x
   - [Pandoc](http://johnmacfarlane.net/pandoc/) >= 1.12.0.2

Please clone the [Substance Tutorial](https://github.com/substance/tutorial) repo, which has the complete code for the examples.

    $ git clone https://github.com/substance/tutorial


Turn a Markdown file into a Substance Article {#convert}
=====================================================


Here comes the first lesson. Let's suppose we have a markdown document `lorem_ipsum.md` that we'd like to turn into a [Substance.Article](http://github.com/substance/article). Substance ships with its own [converter](http://github.com/substance/converter) module, which makes use of Pandoc, a universal document conversion tool. Let's create a little node program that takes a Markdown file as an input, turns it into a Substance Article and stores the resulting JSON in a new file.

## Setup

With your console navigate to the first lesson.

    $ cd 001-convert-md-to-substance

Pull-in dependencies using NPM.

$ npm install

## Procedure

Now take a glance at the `convert.js` file. That's all you need for a simple conversion tool, by just delegating the hard work to the Substance.Converter, and of course Pandoc.

    var fs = require('fs');
    var Converter = require("substance-converter");

    // Parse command line arguments
    // -----------

    var inputFile = process.argv[2];
    var outputFile = process.argv[3];

    // Read markdown input
    // -----------

    var inputDoc = fs.readFileSync(inputFile, "utf8");

    // Do the converstion
    // -----------

    var converter = new Converter();

    converter.convert(inputDoc, 'markdown', 'substance', function(err, doc) {
      if (err) {
        return console.error(err);
      }
      fs.writeFileSync(outputFile, JSON.stringify(doc, null, '  '));
    });

Call your node program, to finally perform the conversion.

    $ node convert.js lorem_ipsum.md lorem_ipsum.json


Great. Now do the same with your very own Markdown document. If you don't get to convert your markdown file, please let us know in the [issue tracker](https://github.com/substance/converter/issues).


Present your article {#display}
=====================================================

In collaboration with [eLife](http://elifesciences.org), we have developed an interactive reader for scientific documents which is based on the Substance Document Model, [eLife Lens](http://lens.substance.io). In this lesson we'll be displaying your freshly generated Substance Article using a customized build of eLife Lens, the [Substance.Reader](http://github.com/substance/reader).

## Setup

Navigate to lesson 2.

    $ cd 002-display-document

The folder contains a stable build of the `Substance.Reader`. Since the document is loaded via AJAX, you just need to serve the folder through a webserver. The probably easiest way to do this is starting Python's SimpleHTTPServer, that ships with most operating systems.

    $ python -m SimpleHTTPServer

Open your browser and navigate to `http://localhost:8000`. You should see a default document ([Figure 1](figure_1)).

## Procedure

Now store a copy of your Substance document in the data folder (e.g. `data/mydoc.json`. You also need to adjust `index.html` so it points to your document like so:

    var app = new Substance({
      // Endpoint must have CORS enabled, or file is served from the same domain as the app
      document_url: "http://example.com/path/to/any-substance-doc.json"
    });



Create a customized renderer {#renderer}
=====================================================

Displaying the document in the official Substance.Reader is great, but what if you wanted to present your article in a more customized fashion?

You don't have to write it from scratch. You can utilize [Substance.Surface](http://github.com/substance/surface) which powers our reader and editor.


## Setup

Navigate to lesson 3.

    $ cd 003-customized-renderer

Again start our little Python server.

    $ python -m SimpleHTTPServer


## Procedure

Using the Substance Surface is really easy. The first thing to do is constructing a `Substance.Article` based on our JSON input. Again, you need to adjust `index.html`:

    var doc = Substance.Article.fromSnapshot(loremIpsumDoc);

A Substance document stores multiple views on its content ([Figure 2](figure_2)). In our case we're interested in the `content` view. Therefore we create a `Document.Controller` instance that we need to paramatrize the `Surface`.

    var docCtrl = new Substance.Document.Controller(doc, {
      view: "content"
    });

Now we are ready to create the Substance.Surface instance.

    var surface = new Substance.Surface(docCtrl, {
      editable: false
    });

Let's wait until the DOM is ready and then render the document and attach it to the body element.

    $(function() {
      $('body').append(surface.render().el);
    });

The markup that is produced by the Surface using the `Substance.Article` definition is pretty straight forward ([Figure 3](figure_3)). 

You can easiliy come up with your very own CSS styles. For instance let's add some styles for headings in `article.css`:

    .surface.content .content-node.heading {
      font-weight: bold;
      color: #0089D3;
    }

    .surface.content .content-node.heading.level-1 {
      font-size: 25px;
    }

A more complete functioning codebase is located in the `index.html` file and `article.css`.






