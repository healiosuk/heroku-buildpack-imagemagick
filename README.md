This is a forked and modified version of the [Heroku ImageMagick buildpack](https://github.com/ello/heroku-buildpack-imagemagick) with the PDF policy enabled to fix [this bug](https://app.asana.com/0/456595238006296/872243800492503).


heroku-buildpack-imagemagick
=================================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for vendoring the ImageMagick binaries into your project.

## How it works
Rather than pulling down binary dependencies from a package manager and extracting them into place, this buildpack compiles Imagemagick from source the first time an app is built with it. The compiled binaries are cached for future builds, so this penalty is only incurred once.

This has the downside of a (potentially very long) deploy time for the first push, with the benefit of a less-fragile build product that's somewhat less likely to break due to platform and dependency shifts. Or at least, that's the hope!

## Stack compatibility
This buildpack is tested primarily against the `cedar-14` stack. Currently, a workaround is required to make it work on the newer `heroku-16` stack - see https://github.com/ello/heroku-buildpack-imagemagick/pull/17 for details.
