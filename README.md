# Web and design team practices

A collection of documents that describe best practices for Canonical web team.

These can be also be viewed at https://canonical-webteam.github.io/practices/.

## Run site locally

This site is built using [Jekyll](https://jekyllrb.com/).

To run this site locally, you'll need to first [install Ruby](https://www.ruby-lang.org/en/documentation/installation/) on your local machine.

Once you have installed Ruby, you can then install [Bundler](https://bundler.io) by running;

```
gem install bundler -v 1.17.3
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

## Troubleshooting

### Jekyll not found
If you encounter a problem when trying to run an installed **gem**, that states that it can not be found, make sure that the directory in which **gems** are installed is included in your PATH.
You can verify this by typing `echo $PATH` in a terminal and checking for the folder in the output.
If you are not sure what folder your **gems** are installed into, run `gem env | grep EXECUTABLE\ DIRECTORY` and add the path that is printed into your PATH environment variable.

## License

The content of this project is licensed under the Creative Commons Attribution-ShareAlike 4.0 International license, and the underlying code used to format and display that content is licensed under the LGPLv3 by Canonical Ltd.
