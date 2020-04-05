# nobrew

## Motivation

Around https://github.com/pyenv/pyenv/issues/839, [pyenv](https://github.com/pyenv/pyenv) was changed to dynamically
detect the presence of an updated homebrew openssl@1.1 when installing Python. Additionally, the Python build recipes were
annotated to call out [support for openssl@1.1](https://github.com/pyenv/pyenv/commit/0708c6c9686268073a3060e01c365a50dd1d4c95#diff-829bd38e9096ee1ba2d562d4b79d392a)
leaving the remainder to fall back to homebrew openssl@1.0.

Later, openssl@1.0 was deprecated (https://brew.sh/2019/11/27/homebrew-2.2.0/) leaving the older Python
build recipes that relied on homebrew openssl@1.0 stranded.


## Use

By way of example, there is no straightforward way to invoke `pyenv install 2.7.10` without triggering
a `brew --prefix openssl` search that finds the incompatible openssl@1.1. The `nobrew` utility provides a way
to hide the homebrew installation so that the Python installation can be triggered normal way:

    nobrew pyenv install 2.7.10

## Installation

To install `nobrew` in `~/bin`:

    cd "$(git rev-parse --show-toplevel)" && ln -s "$PWD/bin/brew" "$HOME/bin"
