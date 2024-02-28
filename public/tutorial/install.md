# Installation of `CInet::Tools`

The code for conditional independence computations behind this website and
data sets is written in Perl. You will need a relatively recent version of
it, at least `v5.26` and various dependencies.

We offer a `Containerfile` which can be used with [Docker] or [podman] to
create an image based on Arch Linux on which all dependencies and all CInet
modules are automatically installed.

- If you want to download the `Containerfile` and build the image yourself,
  see the instructions on [GitHub](https://github.com/CInet/container).
- Alternatively, you can download our pre-built image
  [`cinet-all.tar.zst`](/images/cinet-all.tar.zst)
  <small style="line-break: anywhere">(for checksum, see [`sha256sums.txt`](/images/sha256sums.txt))</small>
  and load it into podman (or Docker) using `zstdcat cinet-all.tar.zst | podman load`.

After the image is installed on your computer, it is easy to start an
interactive `CImake` shell for computations using `CInet::Tools`:

``` console
$ podman run -it cinet/all bash -lc CImake
0> Gaussoids(4)->count
679
```

If you do not want to use Docker or podman, you can execute the steps in the
`Containerfile` by yourself. They are, however, specific to Arch Linux. Names
of dependencies will vary for other Linux distributions.

Here are some tips for the manual installation:

- If your Perl version is not recent enough, I recommend you use [`perlbrew`]
  to compile your own recent Perl. `perlbrew lib create` can be used to create
  a local library in your home directory into which CPAN modules are installed.
  This will require a C compiler and other standard build tools.
- I also recommend to use [`cpanm`] for module installations. It can be
  conveniently installed through `perlbrew install-cpanm`.
- The rule of thumb in CInet is to prefer to bundle source code of native
  programs or libraries in so-called `Alien` modules. For example,
  [`CInet::Alien::CaDiCaL`] bundles the SAT solver [CaDiCaL], which is
  used by [`CInet::Propositional`]. You need native build tools, including
  a C++ compiler, to build these modules.
- This installation will take a while, especially if you have never used
  Perl and CPAN before, because there is a sizable number of transitive
  dependencies. The effort has to be spent only once. When you update
  `CInet::Tools` later, most dependencies are already in place and it will
  go much faster.

During installation, various test suites run to ensure (as far as the
test suites go) that the modules function properly on your system.
If you encounter any bugs or believe this guide is incomplete, then
please do not hesitate to write me an email via [Contact](/contact)!

[Docker]: https://www.docker.com
[podman]: https://podman.io
[`perlbrew`]: https://perlbrew.pl
[`cpanm`]: https://metacpan.org/pod/App::cpanminus
[`local::lib`]: https://metacpan.org/pod/local::lib
[`CInet::Alien::CaDiCaL`]: /doc/CInet::Alien::CaDiCaL
[CaDiCaL]: http://fmv.jku.at/cadical/
[`CInet::Propositional`]: /doc/CInet::Propositional
