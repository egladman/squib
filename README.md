# squib

A surprisingly capable albeit excruciatingly slow static site generator written in Bash 4.0+.

### Why
While writing [crunchwrap](https://github.com/egladman/crunchwrap) (for a seperate project) I came to realization that with a few more LOC I could have my very own static site generator. This quickly snowballed into the project you see today as I kept adding features. Inspired by [Jekyll](https://github.com/jekyll/jekyll); Squib has no business working as well as it does.

### Retrospect
Squib doesn't really bring anything new to the table besides the Bash gimmick. Markdown support is optional because it depends on Daring Fireball's original Perl implementation. Markdown support is a staple feature in most blog platforms these days. This begs the question, if I'm having to depend on an entirely different language for a 'feature complete' experience what justifies me writing squib in a shell? Nothing, but that obviously didn't stop me.

I'll be the first to admit, there are much better alternatives out there that doen't depend on Bash of all things. Many of squib's design decisions were made to skirt around the limitations of Bash. Squib should've been written in literally any other language, but where's the fun in that.

### Quick Start

Create project scaffolding in the working directory
```
squib init
```
---

Performs a one off build of your website to `site`
```
squib build
```
---

Builds your website any time a source file changes
```
squib build --watch
```

---

Shows help
```
squib --help
```

### Tips

Use github pages? Don't forget to configure the baseurl.
```
build --watch --baseurl /myproject #https://egladman.github.io/myproject
```
---

Don't want to spin up a webserver for development? Cheat by using absolute paths. It kinda works...
```
squib build --watch --baseurl $(pwd)/site
```

---

Spin up a local server with a perl one-liner. If you've opted to use Markdown then you're good to go.
```
perl -MHTTP::Server::Brick -e '$s=HTTP::Server::Brick->new(port=>8080); $s->mount("/"=>{path=>"site"}); $s->start'
```

*Note:* The easiest way to install module `HTTP::Server::Brick` is with `cpanm` or `cpan`

### Install

```
git clone git@github.com:egladman/squib.git
cp squib/squib /usr/local/bin/squib
```

#### Dependencies

- [crunchwrap](https://github.com/egladman/crunchwrap) - A templating engine written in pure Bash
- Self-loathing. *Why else would you be considering using a static site generator written in **Bash**.*
- GNU Coreutils - `sha1sum` `cat` `cut`
- GNU findutils - `find`

*Note:* I have yet to test against non gnu utilities. The long-term goal is have 100% compatability with BSD variants. Until that happens presume incompatability. Submit an issue with your finding/results.

#### Optional Dependencies

- [Markdown](https://github.com/bobtfish/text-markdown) - Install via `cpan` or with your system package manager. (i.e. `dnf install perl-Text-Markdown`)

*Note:* If you choose not to install Markdown your blog posts must be written in html.
