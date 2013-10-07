In this tutorial you'll learn:

1. How to [convert](convert) a markdown file into a Substance Article
2. [Display](display) Substance content in our interactive reading environment.
3. Create a customized [renderer](renderer)
4. [Submit](publish) a publication to Substance.io

Substance is a work-in-progress by design. We'd like avoid the lock-in phenomenon and design a system that can deal with the ever-changing needs of its users. We don't propose a one-size fits it all solution. Instead we'd like to encourage you to take the pieces you need and build your very own publishing system. We're glady reviewing your adaptions and include them in the core system when it makes sense.

# Preprations

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

Let's suppose we have a markdown document `hello-world.md` that we'd like to turn into a [Substance.Article](http://github.com/substance/article). Substance comes with its own converter, available as a separate module. It makes use of Pandoc, a universal document converter. Let's create a little node program that takes a markdown file as an input, turns it into a Substance Article and stores it on the disk.

## Setup
  
With your console navigate to lesson 1.

$ cd 001-convert-md-to-substance

Pull-in dependencies using the Substance Screwdriver.

$ substance --update

## Implementation

Now take a glance at the `convert.js` utility. That's all you need for a simple conversion tool, by just delegating work to the Substance.Converter.

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

    $ node convert.js hello-world.md hello-world.json










# Present your content {#display}

## Intro

In collaboration with eLife, we have developed an interactive reader for scientific documents which is based on the Substance Document Model, [eLife Lens](http://lens.substance.io). In this lesson we'll be displaying our fresh `hello-world.json` document using a customized build of eLife Lens, the Substance.Reader. You'll be able to drop

## Setup

Navigate to lesson 2.

    $ cd 002-display-document

The folder contains a stable build of the Substance.Reader. Since the document is loaded via AJAX, you just need to serve the folder through a webserver. The probably easiest way to do this is starting Python's SimpleHTTPServer, that's included in most operating systems.

    $ python -m SimpleHTTPServer

Open your browser and navigate to `http://localhost:8000`

## Implementation

All you need to do now is replacing data/document.json with your own freshly converted Substance Article.












# Create a customized renderer {#renderer}

This lesson is not yet ready.









# Publish your document on Substance.io {#publish}

1. Fork the `substance/io` project on Github.
2. Start the server
3. Add your document to the docs folder. (Use your favorite text editor)
4. Commit your changes
5. Submit a Pull Request on Github
