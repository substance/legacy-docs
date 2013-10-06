In this tutorial you'll learn:

1. How to convert a markdown file into a Substance Article
2. Display Substance content in our reading environment.
3. Create a customized renderer
4. Submit a publication to Substance.io
5. Launch your very own Substance document repository

Substance is a work-in-progress by design. We'd like avoid the lock-in phenomenon and design a system that can deal with the ever-changing needs of its users. We don't propose a one-size fits it all solution. Instead we'd like to encourage you to take the pieces you need and build your very own publishing system. We're glady reviewing your adaptions and include them in the core system when it makes sense.

# Prerequisites

   - Node.js >=0.10.x
   - [Pandoc](http://johnmacfarlane.net/pandoc/) >= 1.12.x

Please fork and clone the [Substance Tutorial](https://github.com/substance/tutorial) repo.

    $ git clone https://github.com/your_user/substance-tutorial

During the tutorial we'd like to encourage you to review the contents of the tutorial. If you spot an error please just fix it, push it to your fork and file a pull request on Github.

# Turn a markdown file into a Substance Article

## Intro

Let's suppose we have a markdown document `hello-world.md` that we'd like to turn into a Substance.Article. Substance comes with its own converter, available as a separate module. It makes use of Pandoc, a universal document converter. Let's create a little node program that takes a markdown file as an input and returns a Substance compatible piece of JSON.

## Setup
  
    - Node.js >=0.10.x
    - [Pandoc](http://johnmacfarlane.net/pandoc/) >= 1.12.x

    Module management, Substance screwdriver or NPM?

## Implementation

    var Converter = require("substance-converter");
    var ConverterServer = require("substance-converter/src/server");
    var fs = require('fs');
    var helloDoc = fs.readFileSync(__dirname + "/hello-world.md", "utf8");
    var converter = new ConverterServer();

    converter.convert(helloDoc, 'markdown', 'substance', function(err, doc) {
      if (err) {
        console.error(err);
      }

      fs.writeFileSync(__dirname + "/hello-world.json", JSON.stringify(doc, null, '  '));
    });

Now call your node program.

    $ node convert.js hello-world.md hello-world.json

# Make your content available to readers

## Intro

In collaboration with eLife, we have developed an interactive reader for scientific documents which is based on the Substance Document Model, [eLife Lens](http://lens.substance.io). In this lesson we'll be displaying our fresh `hello-world.json` document using a customized build of eLife Lens, the Substance.Reader. You'll be able to drop

## Setup

No setup required

## Implementation

The implementation here is really easy. Just download a customized 

# Create a customized renderer

This lesson is not yet ready.

# Submit a publication to Substance

1. Fork the `substance/io` project on Github.
2. Start the server
3. Add your document to the docs folder. (Use your favorite text editor)
4. Commit your changes
5. Submit a Pull Request on Github

# Launch your own Substance-based blog {#section_2}

Lorem ipsum dolor sit amet ([Figure 1](figure_1)), consectetur adipiscing elit. Donec bibendum vel dui sed lobortis. Praesent vitae commodo felis. Maecenas faucibus pellentesque sapien nec ullamcorper. In mattis risus vitae nulla fermentum elementum. Nulla at sagittis urna, vel tincidunt felis. Nunc a semper tortor (see [Section 3](section_3)). Vivamus faucibus gravida eros sed luctus ([Table 1](table_1)). Sed vulputate mauris nec augue dignissim varius.

# Section 3 {#section_3}

Fusce mattis ultricies mauris et rhoncus (see [Section 2](section_2)). Vestibulum auctor arcu turpis, eu sagittis dolor dapibus non. Mauris hendrerit eros eget arcu accumsan imperdiet. Aenean orci mauris, pulvinar non arcu vel, posuere vestibulum purus. Praesent ut ligula neque. Nullam ac leo augue. Fusce rutrum ligula est, egestas adipiscing libero faucibus in.
