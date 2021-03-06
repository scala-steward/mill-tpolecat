## mill-tpolecat

[![Build Status](https://api.travis-ci.org/DavidGregory084/mill-tpolecat.svg)](https://travis-ci.org/DavidGregory084/mill-tpolecat)
[![License](https://img.shields.io/github/license/DavidGregory084/mill-tpolecat.svg)](https://opensource.org/licenses/Apache-2.0)
[![Latest Version](https://img.shields.io/maven-central/v/io.github.davidgregory084/mill-tpolecat_2.13.svg)](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22io.github.davidgregory084%22%20AND%20a%3A%22mill-tpolecat_2.13%22)

### scalac options for the enlightened

mill-tpolecat is an extension for the [Mill build tool](https://github.com/lihaoyi/mill/) which configures your scalac options according to [@tpolecat](https://github.com/tpolecat)'s [recommendations](https://tpolecat.github.io/2017/04/25/scalac-flags.html) where possible, according to the Scala version you are using.

This should help to ensure that you are getting the greatest possible benefit from the Scala compiler's many linting options.

It has been tested with version 0.9.3 of mill.

### Usage

Import the module in `build.sc` using mill's `$ivy` import syntax, and extend `TpolecatModule` in your build definition:

```scala
// build.sc

import $ivy.`io.github.davidgregory084::mill-tpolecat:0.2.0`

import io.github.davidgregory084.TpolecatModule

object core extends TpolecatModule {
  def scalaVersion = "2.12.11"
}
```

If necessary you can filter out scalac options that are not appropriate for your project:

```scala
// build.sc

import $ivy.`io.github.davidgregory084::mill-tpolecat:0.2.0`

import io.github.davidgregory084.TpolecatModule

object core extends TpolecatModule {
  def scalaVersion = "2.12.11"
  def scalacOptions = T { super.scalacOptions().filterNot(Set("-Yno-imports")) }
}
```

### Caveat

I can't promise this plugin will work for old minor releases of Scala. It has been tested with:

* 2.13.2
* 2.12.11
* 2.11.12

### License

All code in this repository is licensed under the Apache License, Version 2.0.  See [LICENSE](./LICENSE).
