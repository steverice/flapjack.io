This is the entire site and documentation for [flapjack.io](http://flapjack.io) and [packages.flapjack.io](http://packages.flapjack.io)

# flapjack.io

## Building

From your checkout of the [Flapjack.io repository](https://github.com/flapjack/flapjack.io):

``` bash
bundle exec middleman build
bundle exec middleman server
```

Middleman will monitor all files in source/ and trigger a build on change.

View your changes at [http://localhost:4567/](http://localhost:4567/).

## Publishing

When you want to push updated documentation to [flapjack.io](http://flapjack.io/), run:

``` bash
# stop the middleman server if it's running and then:

git commit
git push
rm -rf build && bundle exec rake publish
```

This will build the content from source/ and copy the files to the gh-pages branch on GitHub.

## Default version

The default version of the documentation is specified in the config.rb in the top-level directory.

To update all the links, update the following variables:

```
set :default_version, 1.0
set :layout, "1.0"
```

# packages.flapjack.io

Refer the [README](https://github.com/flapjack/flapjack.io/blob/master/source/packages.flapjack.io/README.md) under [source/packages.flapjack.io](https://github.com/flapjack/flapjack.io/blob/master/source/packages.flapjack.io/)

