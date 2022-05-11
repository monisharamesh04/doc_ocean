#

## Commands

: `$ mkdocs new [dir-name]` - Create a new project.
: `$ mkdocs serve` - Start the live-reloading docs server.
: `$ mkdocs build` - Build the documentation site.
: `$ mkdocs help` - Print this help message.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.

## Upgrade Mkdocs

: `$ pip3 install --upgrade mkdocs mkdocs-material`
: `$ cd mkdocsDir`
: `$ mkdocs build --clean`

## Reverting to an older version of Mkdocs

: `$ pip install mkdocs==0.16.1 mkdocs-material==1.2.0`

## Deploy to the github page

: `$ mkdocs gh-deploy`
