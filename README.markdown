# Go bindings to system LLVM

This library provides bindings to a system-installed LLVM.

Currently supported:

  * LLVM 15 and 14 from [apt.llvm.org](http://apt.llvm.org/) on Debian/Ubuntu.
  * LLVM 15 and 14 from Homebrew on macOS.
  * LLVM 15 with a manually built LLVM through the `byollvm` build tag. You
    need to set up `CFLAGS`/`LDFLAGS` etc yourself in this case.

You can select the LLVM version using a build tag, for example `-tags=llvm14`
to use LLVM 14.

## Usage

If you have a supported LLVM installation, you should be able to do a simple `go get`:

    go get tinygo.org/x/go-llvm

After downloading, you may have to update the configuration for your system:

    make config

If you built your own LLVM, you can also use that:

    # update LLVM files
    make update SRCDIR=<dir>
    
    # configure this LLVM build
    make config BUILDDIR=<builddir>

Note that you may have to comment out parts of `backports.go` if you use a
newer version of LLVM.

## License

Most of the files are extracted from the LLVM source tree, specifically all
\*.go, \*.cpp, and \*.h files come directly from
[bindings/go/llvm](https://github.com/llvm-mirror/llvm/tree/release_80/bindings/go/llvm)
in the LLVM source tree. They are all released under the [Apache License 2.0
(with LLVM exceptions)](http://releases.llvm.org/9.0.0/LICENSE.TXT). Check
upstream LLVM for detailed copyright information.

This README, the backports\* files, and the Makefile are separate from LLVM but
are licensed under the same license.
