# Axioms and CI inference

After [installing `CInet::Tools`](/install), you can start the program `CImake`:

``` console
$ CImake
0> 
```

This presents you with a REPL (read-eval-print loop) for you to enter
Perl code, similar to [`polymake`]. The REPL is just an interface to a
standard Perl interpreter with all the CInet modules loaded.

Using [`CInet::Propositional`], axioms for CI structures can easily
be written down. Let's define semigraphoids and determine their counts:

``` console
0> propositional Semigraphoids = cube (ijk|L) -> (ij|L) & (ik|jL) => (ik|L) & (ij|kL);
1> Semigraphoids(3)->count
$res[0] = 22
2> Semigraphoids(4)->count
$res[1] = 26424
```

[`polymake`]: https://polymake.org/doku.php
[`CInet::Propositional`]: /doc/CInet::Propositional
