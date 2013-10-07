Welcome to the official Substance Tutorial. You'll learn:

1. How to [convert](convert) a markdown file into a Substance Article
2. [Display](display) Substance content in our interactive reader.
3. Create a customized [renderer](renderer)
4. [Submit](publish) a publication to Substance.io

# Preparations

Make sure you have the following software packages installed on your computer before starting over with the tutorial.

   - Node.js >=0.10.x
   - [Pandoc](http://johnmacfarlane.net/pandoc/) >= 1.12.x

Please fork and clone the [Substance Tutorial](https://github.com/substance/tutorial) repo.

    $ git clone https://github.com/your_user/substance-tutorial

During the tutorial we'd like to encourage you to review the contents of the tutorial. If you spot an error please just fix it, push it to your fork and file a [Pull Request](https://help.github.com/articles/using-pull-requests) on Github.


Throughout our tutorial we are using the [Substance Screwdriver](http://github.com/substance/screwdriver) to manage dependencies. The tutorial always runs against the latest stable dev versions. Please note that for all official releases we also provide [NPM](http://npmjs.org/) packages.
  
    $ git clone https://github.com/substance/screwdriver.git
    $ cd screwdriver
    $ sudo python setup.py install

Now you should be able to run the `substance` program from the command line.

    $ substance --help










# Turn a markdown file into a Substance Article {#convert}

Here comes lesson one. Let's suppose we have a markdown document `lorem_ipsum.md` that we'd like to turn into a [Substance.Article](http://github.com/substance/article). Substance comes with its own converter, available as a separate module. It makes use of Pandoc, a universal document conversion tool. Let's create a little node program that takes a markdown file as an input, turns it into a Substance Article and stores it on the disk.

## Setup
  
With your console navigate to the first lesson.

    $ cd 001-convert-md-to-substance

Pull-in dependencies using the Substance Screwdriver.

$ substance --update

## Implementation

Now take a glance at the `convert.js` utility. That's all you need for a simple conversion tool, by just delegating the hard work to the Substance.Converter, and of course Pandoc.

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

Now call your node program.

    $ node convert.js lorem_ipsum.md lorem_ipsum.json


Great. Now try the same with your very own markdown file.






# Present your content {#display}

In collaboration with eLife, we have developed an interactive reader for scientific documents which is based on the Substance Document Model, [eLife Lens](http://lens.substance.io). In this lesson we'll be displaying your freshly generated Substance Article using a customized build of eLife Lens, the Substance.Reader. 

## Setup

Navigate to lesson 2.

    $ cd 002-display-document

The folder contains a stable build of the Substance.Reader. Since the document is loaded via AJAX, you just need to serve the folder through a webserver. The probably easiest way to do this is starting Python's SimpleHTTPServer, that's included in most operating systems.

    $ python -m SimpleHTTPServer

Open your browser and navigate to `http://localhost:8000`. You should see a default document ([Figure 1](figure_1)).

## Implementation

All you need to do is storing a copy of your Substance document in the data folder (e.g. `data/mydoc.json`. You also need to adjust `index.html` so it points to your document like so:



    var app = new Substance({
      // Endpoint must have CORS enabled, or file is served from the same domain as the app
      document_url: "http://example.com/path/to/any-substance-doc.json"
    });








# Create a customized renderer {#renderer}

This lesson is not yet ready.









# Publish your document on Substance.io {#publish}

This lesson is not yet ready.
