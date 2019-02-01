# Web and design team practices

A collection of documents that describe best practices for Canonical web team.

These can be also be viewed at https://canonical-webteam.github.io/practices/.

## Run site locally

This site is built using [Jekyll](https://jekyllrb.com/).

To run this site locally, you'll need to first [install Ruby](https://www.ruby-lang.org/en/documentation/installation/) on your local machine.

Once you have installed Ruby, you can then install [Bundler](https://bundler.io) by running;

```
gem install bundler
```

The next step is to install the Ruby gems required to run the site with Bundler;

```
bundle install
```

You can then serve the site using Jekyll;

```
jekyll serve
```

...which should open the site locally in your browser at http://127.0.0.1:4000/practices/

## Contributing

For guidelines on contributing to these documents, see [CONTRIBUTING.md](CONTRIBUTING.md).
