# squib

A surprisingly capable albeit slow static site generator written in Bash 4.0+.

### Why
While writing [crunchwrap](https://github.com/egladman/crunchwrap) for another project I came to realization that with a few more LOC I could have my very own static site generator. This quickly snowballed into the project you see today as I kept adding features.

### Retrospect
Squib doesn't really bring anything new to the table besides the Bash novelity. Markdown support is optional because it depends on Daring Fireball's original Perl implementation. I much prefer writing markdown over html. This begs the question, if I'm having to depend on another language to in order to have a 'feature complete' experience what business do I have writting this in Bash to begin with? None, but that obviously didn't stop me. I'll be the first to admit, there are much better alternatives out there that aren't shackled by their written language. Many of squib's design decisions were made to skirt around my perceived limitations of Bash.

### Quick Start

Create project scaffolding in the working directory
```
squib init
```

Performs a one off build of your website to `site`
```
squib build
```

Builds your website any time a source file changes
```
squib build --watch
```

Shows help
```
squib --help
```

### Install

```
git clone git@github.com:egladman/squib.git
cp squib/squib /usr/local/bin/squib
```

#### Dependencies

- [crunchwrap](https://github.com/egladman/crunchwrap)
  - A templating engine written in pure bash

- GNU coreutils
  - `sha1sum`, `cat`, `cut`

- GNU findutils
  - `find`

*Note:* I have yet to test against non gnu utilities. The long-term goal is have 100% compatability with BSD variants. Until that happens presume incompatability. Submit an issue with your finding/results.

#### Optional Dependencies

- [Markdown](https://github.com/bobtfish/text-markdown)
  - You can install via `cpan` or with your system package manager. (i.e. `dnf install perl-Text-Markdown`)
  - If you choose not to install Markdown your blog posts must be written in html.
