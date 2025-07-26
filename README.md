# hugo-playground

Hugo playground

- [References](#references)
- [Editions](#editions)
- [Installation](#installation)
  - [Binary](#binary)
  - [Source](#source)

## References

- [https://gohugo.io/](https://gohugo.io/)
- [https://github.com/gohugoio/hugo](https://github.com/gohugoio/hugo)

## Editions

Adapted from [https://github.com/gohugoio/hugo](https://github.com/gohugoio/hugo):

- **Hugo** is available in three editions
  - **Standard**: provides core functionality
  - **Extended**: offers advanced features
  - **Extended/deploy**: offers advanced features
- Unless your specific deployment needs require the extended/deploy edition, **we recommend the extended edition**.

## Installation

### Binary

I'm using this method:

- Go to [https://github.com/gohugoio/hugo/releases](https://github.com/gohugoio/hugo/releases)
- Choose the most recent one [https://github.com/gohugoio/hugo/releases/tag/v0.148.1](https://github.com/gohugoio/hugo/releases/tag/v0.148.1)
- Download [https://github.com/gohugoio/hugo/releases/download/v0.148.1/hugo_extended_0.148.1_linux-amd64.tar.gz](https://github.com/gohugoio/hugo/releases/download/v0.148.1/hugo_extended_0.148.1_linux-amd64.tar.gz)
- Check the sha256sum
- The TGZ has 3 files:
  - hugo
  - README.md
  - LICENSE
- Copy **hugo** binary to **/usr/local/bin**

Result:
```
$ hugo version
hugo v0.148.1-98ba786f2f5dca0866f47ab79f394370bcb77d2f+extended linux/amd64 BuildDate=2025-07-11T12:56:21Z VendorInfo=gohugoio
```

**Optional**: use **hugo completion** support to setup shell autocompletion

### Source

My environment:

- Linux Mint 22.1 Cinnamon
- go version go1.24.5 linux/amd64
- gcc (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0

Using [https://github.com/gohugoio/hugo](https://github.com/gohugoio/hugo) as a reference:

- Build the standard edition:
```
go install github.com/gohugoio/hugo@latest
```
- Build the extended edition (I tried this: 2 minutes on i7):
```
CGO_ENABLED=1 go install -tags extended github.com/gohugoio/hugo@latest
```
- Build the extended/deploy edition:
```
CGO_ENABLED=1 go install -tags extended,withdeploy github.com/gohugoio/hugo@latest
```

Result:
```
$ hugo version
hugo v0.148.1+extended linux/amd64 BuildDate=unknown
```
