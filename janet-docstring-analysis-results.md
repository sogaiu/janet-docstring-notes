## Background

The Janet source code of janet, spork, and > 500 repositories was
analyzed for usage of certain "janet docstring" features.

## Explanation of Listed Content

For each feature, what is listed includes:

* A name
* A quantitative indicator `(L / U)` of intended / unintended
  occurences
* List of repositories that use the feature (including in most cases
  the likely corresponding author)

The quantitative indicator is of the form `(L / U)`, where:

* `L` - number (sometimes estimate) of legitimate uses
* `U` - number of unintended triggers (parser thinks a feature was
  used while author probably didn't intend)

## Summary

* By far the most used features are:
  * top-level paragraphs `(> 8000 / ?)`
  * code spans `(> 4000 / ?)`
* Trailing a fair bit, but possibly used somewhat often include:
  * unordered lists `(182 / 1)`
  * fenced code blocks `(110 / 0)`
* High unintentional use features include:
  * indented code blocks `(11 / 92)`
  * italics `(15 / 54)`
  * underline `(3 / 58)`
* Although strictly speaking, loose lists don't seem to be quite
  supported, they did see some use `(8 / 0)`, in particular, more than
  nested lists `(5 / ?)` and underline `(3 / 58)`

## Supported Features 

* top-level paragraphs `(> 8000 / ?)`

  * janet (bakpakin)
  * spork
  * ...many projects

* code spans `(> 4000 / ?)`

  * janet (bakpakin)
  * spork
  * ...many projects

* unordered lists `(182 / 1)`

  * argy-bargy (pyrmont)
  * breakout (pepe)
  * cartnet (yumaikas)
  * doozer (subsetpark)
  * fantasy-console-carts (alect)
  * freja-layout (saikyun)
  * fugue (subsetpark)
  * gp (pepe)
  * janet-evemu (czkz)
  * janet-libMPSSE (strangepete)
  * janetsh (andrewchambers)
  * jnj (subsetpark)
  * joule-editor (CFiggers)
  * journo (CFiggers)
  * junk-drawer (AlecTroemel)
  * juno (CFiggers)
  * neil (pepe)
  * pantagruel (subsetpark)
  * saikyun (freja-layout)
  * shawn (pepe)
  * spork
  * strangepete (janet-libMPSSE)
  * trane (gwegash)
  * whist (subsetpark)

* fenced code blocks `(110 / 0)`

  * bagatto (subsetpark)
  * bauble (ianthehenry)
  * cy (cfoust)
  * doozer (subsetpark)
  * freja-layout (saikyun)
  * fugue (subsetpark)
  * j3blocks (amano.kenji)
  * jnj (subsetpark)
  * jurl (cosmictoast)
  * small-peg-tracer (sogaiu)
  * tomlin (pyrmont)
  * trane (gwegash)

* bold `(26 / 0)`

  * fugue (subsetpark)
  * tomlin (pyrmont)
  * trane (gwegash)

* ordered lists `(21 / 0)`

  * bagatto (subsetpark)
  * jpm (bakpakin)
  * fugue (subsetpark)
  * junk-drawer (AlecTroemel)
  * musty (pyrmont)
  * testament (pyrmont)

* italics `(15 / 54)`

  * bagatto (subsetpark)
  * bauble (ianthehenry)
  * coq-build-toolkit (gamma-delta)
  * doozer (subsetpark)
  * fugue (subsetpark)
  * osprey (swlkr)
  * pantagruel (subsetpark)
  * paula (pepe)
  * spork

* indented code blocks `(11 / 92)`

  * coq-build-toolkit (gamma-delta)
  * janet (bakpakin)
  * janet-pq (andrewchambers)
  * journo (CFiggers)
  * log-manager (llmII)

* tight nested list `(5 / ?)`

  * gp (pepe)
  * janet-zipper (sogaiu)
  * jurl (cosmictoast)
  * pantagruel (subsetpark)
  * whist (subsetpark)

* underline `(3 / 58)`

  * cy (cfoust)
  * janet (bakpakin)
  * janet-hypertext (louis.jackman)

## Features That Aren't Quite Supported

* loose lists `(8 / 0)`

  * fugue (subsetpark)
  * janet
  * janet-evemu (czkz)
  * janetsh (andrewchambers)

