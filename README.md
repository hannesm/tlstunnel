[![Build Status](https://travis-ci.org/hannesm/tlstunnel.svg?branch=master)](https://travis-ci.org/hannesm/tlstunnel)

Who needs a stunnel if you have a tls tunnel?

`tlstunnel` is picky; it won't accept connections:
- which do not contain the [secure renegotiation](https://tools.ietf.org/html/rfc5746) extension
- which speak SSL version 3
- if the given certificate chain is not valid (or contains an X.509 version 1 certificate, or less than 1024 bits RSA public key

## Installation

You first need [OCaml](https://ocaml.org) (at least 4.1.0) and
[OPAM](https://opam.ocaml.org) (1.2.*) from your distribution.

Then, run `opam repo add mirage-dev
git://github.com/mirage/mirage-dev`. Afterwards, install `tlstunnel`
with `opam install tlstunnel`.

## Execution

A sample command line is:

`tlstunnel -b 127.0.0.1:8080 -f 4433 -cert server.pem`

which listens on TCP port `4433` with the given certificate chain
and private key (both in `server.pem`), and forwards
connections to `127.0.0.1` on port `8080`.

An optional argument is `-l FILE` to log into a file instead of to
stdout.  Try `--help` for all command line arguments.
