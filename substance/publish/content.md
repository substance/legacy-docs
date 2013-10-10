We'd like to invite you to publish guest articles on Substance.io. We'll create new collections on demand to categorize articles coming from the community.

Substance.io is powered by our minimal publishing system, [IO](http://github.com/substance/io). It lets you write articles in Markdown and define figures, tables etc. in a simple JSON syntax. All that input is compiled into a full-fledged Substance Article including the main content, meta information like the title and authors and figures you have specified. It works similarly to [Jekyll](http://jekyllrb.com/), a static site generator written in Ruby. Compiled IO document repositories can be hosted on any webserver. It's just a bunch of static [HTML + JSON](https://github.com/substance/io/tree/master/dist) files.

## Install IO

Installing IO locally is pretty easy using NPM.

    $ npm install substance-io -g

The proposed workflow for adding your own docs is [forking](https://help.github.com/articles/fork-a-repo) the [Substance Docs](http://github.com/substance/docs) repository and running IO against it.

    $ git clone https://github.com/your_user/docs.git
    $ cd docs

Run IO.

    $ io

And point your browser to `http://localhost:5000`

If you want, you can point `io` to a different folder:

    $ io <path-to-library-folder>

To use a different port you would call:

    $ PORT=5123 io


## Add a new collection

Let's suppose you'd like to write an article about Javascript Inheritance. All you need is your favorite text editor.


Let's add a new collection Javascript by just creating a folder `javascript` within the docs folder.

Every collection requires to have some meta-information attached, which are specified in an `index.json` file.

    {
      "name": "Javascript",
      "published": true,
      "updated_at": "2013-11-30",
      "image": "http://example.com/javascript.png",
      "description": "Javascript-related articles."
    }

Now point your browser to `http://localhost:5000/#explore` and you should see the new Javascript collection.

## Add a new document

Each document lives in a folder within the collection. Let's create a folder `docs/javascript/inheritance`. Every document requires to have an `index.json` containing meta-information as well as a `content.md` which has the document's main content.

Our index.json could look like this:

    {
      "title": "Understanding Javascript Inheritance",
      "published": true,
      "published_on": "2013-10-05",
      "collaborators": [
        {
          "name": "John Doe"
        }
      ]
    }

And a sample `content.md`.

    A lesson about JS inheritance.

    1. Constructor functions
    2. prototype
    3. new

You you can preview at any time by refreshing `http://localhost:5000/javascript/inheritance` in your browser.


## Figures

Markdown has limitations when it comes to rich content, e.g. tables and figures. With Substance you can specify figures and tables in a separate file and reference them from your main document using markdown syntax.

Let's add an illustrative figure to our article by creating a `resources.json` file in our article folder.

    {
      "figures": [
        {
          "id": "figure_1",
          "type": "figure",
          "label": "Figure 1",
          "url": "http://example.com/js-inheritance.png",
          "caption": "Illustration describing the functioning of the prototype chain in Javascript"
        }
      ]
    }

Now reference that figure in your main text using its id.

    In Javascript there's a concept called Prototypal Inheritance ([Figure 1](figure_1)).

Soon you'll be able to manage citations as well.

## Submit your article

Commit your changes using Git.

    $ cd docs
    $ git add javascript/inheritance/index.json <...>
    $ git commit
    $ git push origin 0.1.x

Now that you pushed your changes to your fork, the last step is filing a [Pull Request](https://help.github.com/articles/using-pull-requests) on Github. We'll review your submitted article and put it live as soon as possible.