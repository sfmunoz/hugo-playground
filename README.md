# hugo-playground

Hugo playground

- [References](#references)
- [Editions](#editions)
- [Installation](#installation)

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

My environment:

- Linux Mint 22.1 Cinnamon
- go version go1.24.5 linux/amd64
- gcc (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0

Using [https://github.com/gohugoio/hugo](https://github.com/gohugoio/hugo) as a reference:

- Build the standard edition:
```
go install github.com/gohugoio/hugo@latest
```
- (**MY CHOICE**) Build the extended edition (2 minutes on i7):
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
