Test::Mini::Logger::Lapidary
============================

For those developers familiar with Ruby's `test/unit`, or many other
xUnit-style frameworks, Perl's testing landscape may seem a little foreign.
[Test::Mini](http://search.cpan.org/search?query=Test::Mini) aims to help
bridge the gap somewhat by providing a familiar, unordered assertion-based
testing paradigm to Perl.  Those looking for something more friendly than the
default [TAP](http://testanything.org) output, however, will be somewhat
disappointed.

`Test::Mini::Logger::Lapidary` implements a reasonable approximation of the
Ruby `test/unit` output, both for compatibility with the existing tools that
parse _that_ and as an example of what can be done using the existing Logger
API.

`prove`?
--------

Unfortunately, this logger will not play nicely with any of the existing
TAP-aware Perl toolchain.  To run your tests without the help of a harness
script, simply execute the file as any other Perl script, or require the file
from your own test routine.  In `zsh` (and other recursive-glob-aware shells),
the following command will automatically run all of the
`Test::Mini`[<sup>1</sup>](#fn1) tests under `t`.

    perl -I lib -e 'require "$_" for @ARGV' t/**/*.t

To set the logger, set the `TEST_MINI_LOGGER` environment variable to
`Lapidary` (or `Test::Mini::Logger::Lapidary`, if you're a fan of verbosity).

Alternately, if you're only interested in running a single test file (or you
have a more robust test script), you can pass the `--logger` option through,
which will take either of the previously mentioned options.

<a name="fn1"><sup>1</sup></a> Actually, it will load all of the scripts from
`t`; if you have non-`Test::Mini` tests in there, they'll likely run as well.
Which will probably break things.  You've been warned.
