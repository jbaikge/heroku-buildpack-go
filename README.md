# Heroku Buildpak: Go

This is a [Heroku buildpack][buildpack] for Go apps. It
uses the [go command][]. This repository is useful if you
want to inspect or change the behavior of the buildpack
itself. See the [Go Buildpack Quickstart][quickstart]
for a gentle introduction suitable for Heroku users.

## Usage

Example usage for an app already stored in git:

    $ find . -type f -print
    ./Procfile
    ./src/app/app.go
    ./src/hello/hello.go
    ...

    $ heroku create -s cedar --buildpack http://github.com/zeebo/heroku-buildpack-go.git
    ...

    polarna:heroku_test zeebo$ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom buildpack... done
    -----> Go app detected
    -----> Using Go weekly.2012-02-07
    -----> Running go get -v all
    github.com/zeebo/bencode (download)
    github.com/zeebo/bencode
    hello
    app
    -----> Discovering process types
           Procfile declares types -> web
    -----> Compiled slug size is 1.0MB
    -----> Launching... done, v18
           http://growing-lightning-4944.herokuapp.com deployed to Heroku

The buildpack will detect your app as Go if it has a
`.go` file in the `src` directory, or any subdirectory.

## Hacking

To change this buildpack, fork it on GitHub. Push
changes to your fork, then create a test app with
`--buildpack YOUR_GITHUB_URL` and push to it. If you
already have an existing app you may use `heroku config
add BUILDPACK_URL=YOUR_GITHUB_URL` instead of
`--buildpack`.

## Credits

A lot of the work was done by [kr][kr]. I just took what he did, cleaned it up
and made it work with the new go tool in preparation for Go 1.

[buildpack]: http://devcenter.heroku.com/articles/buildpack
[go command]: http://weekly.golang.org/cmd/go/
[quickstart]: https://gist.github.com/4f3e55309f330efa83af
[kr]: https://github.com/kr/heroku-buildpack-go
