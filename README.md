# Janet Docstring Notes

Janet docstrings...what features do they support...supposedly a
"subset of Markdown"...but what does that mean exactly?

Also, how are the features actually being used?

## Background

### Who Are the Users?

Who are the folks that create and edit Janet docstrings?  Surely they
are mostly (if not entirely) developers.  So may be it's reasonable to
suppose their tools are up to certain kinds of editing tasks
(e.g. managing indentation of blocks) which might not be the case for
other users of Markdown-ish languages.

### Why Not All Features?

Not all Markdown / CommonMark features are supported in Janet
docstrings and this makes sense for at least the following reasons:

1. CommonMark is a complex specification and including a full
   implementation in Janet would likely result in bloat [1].

2. Janet docstrings probably wouldn't benefit from all features in the
   CommonMark specification anyway.

### The `doc-format` Function

`doc-format` is a built-in function that is used indirectly by the
`doc` macro.  Janet users might have seen its output when working
via `janet`'s repl, e.g.:

```
$ janet
Janet 1.38.0-b27c830d linux/x64/gcc - '(doc)' for help
repl:1:> (doc pp)


    function
    boot.janet on line 1894, column 1

    (pp x)

    Pretty-print to stdout or (dyn *out*). The format string used is
    (dyn *pretty-format* "%q").


nil
```

Note that the indented portion of the output after the location
information is output from `doc-format`.

Examining the output from `doc-format` for many Janet docstrings can
probably give a sense of what features people may have thought were
supported.  Note that this isn't necessarily the same as what is
supported [2].

## Docstrings in Various Projects

### In Janet Itself

Observing the output of `doc-format` for the docstrings in the source
code of Janet itself, the following features were detected, in order
of decreasing frequency:

* paragraphs
  * top-level
  * in list items within unordered lists
* code spans
* single level unordered tight lists
* indented code blocks
* single level loose lists [2]
* underline (N.B. not a Markdown-feature)

Note that not all supported features are in use, e.g. ordered
lists do have some level of support but no built-in Janet docstring
uses them at the time of this writing.

"Detection" was performed by manual inspection.

(Most docstrings in Janet itself were written by bakpakin, the author
of `doc-format`, so it seems reasonable to suppose that most of the
observed features in the docstrings are actually supported.)

### In 3rd Party Projects

For 3rd party projects, the following is a list of features that were
detected, roughly in order of decreasing frequency:

* paragraphs
  * top-level
  * in list items in unordered lists
* code spans
* unordered tight lists
  * single level
  * nested
* fenced code blocks
* single level ordered lists
* indented code blocks
* headings
* italics
* bold
* single level loose lists
* links
* thematic breaks

"Detection" was performed via a hybrid automation / manual approach.

`doc-format`'s docstring doesn't give details about which Markdown
features are supported.  The janet-lang.org website does specify some
details, but it's unclear how many users are aware of this and perhaps
this is reflected in the differences between the two lists above.

## Observations

It appears that some folks have taken to using some features that are
not supported in Janet docstrings of Markdown / CommonMarks.  This may
be for various reasons likely not limited to:

* Unclear exactly what is suppported

* Didn't seem to break anything when attempted

* Wanted to reuse docstring content in other settings
  (e.g. Documentarian)

This might have drawbacks down the line if what is supported by Janet
docstrings changes.  It also might work against making certain changes
to what is supported.

One conclusion might be that it's better to be clear upfront about
what features are supported with a clear warning as to potential
consequences of straying from what's supported.

Also, if docstrings are ever to support more features, it seems like
the existing features of Markdown / CommonMark constrain what can be
done reasonably.  Possibly one of the less problematic paths is to
only add things that are already in Markdown / Commonmark.  The
alternative of adding some construct that is not in Markdown /
CommonMark seems risky, both from the perspective of future additions
(how to manage potential clashes?) and getting the specific addition
to work smoothly with existing features.

From a maintenance perspective, given how complex Markdown /
CommonMark is though, it may be best to not add any more features.

At least for the docstrings of Janet itself, `doc-format` seems to be
doing a pretty good job.

## Credits

* pyrmont - numerous discussions

## Footnotes

[1] It's a policy that Janet doesn't include 3rd party dependencies
and an independent implementation of CommonMark would not likely be a
good trade-off.

[2] Some of the output from `doc-format` contains text that look like
loose lists were intended, but strictly speaking, Janet docstrings
themselves do not currently support loose lists.

For example, the following:

```
* A

* B

* C
```

gets parsed as three unordered lists, each with a single item, instead
of a single loose list.

It's not apparent in terminal output, but if one examines
`doc-format`'s internals and traces execution, it becomes clear that
parsing yields multiple single item lists.

In this simple case, it may not matter, but if we wanted to break
`doc-format` into two pieces -- e.g. a parsing piece and a rendering
piece -- the parse results may be unexpected if used with other
"renderers" [3].  Also, the parsing difference may manifest itself for
more complicated lists (e.g. those with nesting).

[3] In fact, this repository is actually one of the products of
investigating how some docstrings on janet-lang.org might be rendered
more nicely.  As part of that investigation, one option considered was
to try to split `doc-format` into two pieces as described above.

