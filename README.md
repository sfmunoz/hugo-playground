# hugo-playground

Hugo playground

- [References](#references)
- [Editions](#editions)
- [Installation](#installation)
  - [Binary](#binary)
  - [Source](#source)
- [Quick start](#quick-start)
  - [Add content](#add-content)
  - [Publish](#publish)
- [Themes](#themes)
  - [Git submodule](#git-submodule)
  - [Hugo module](#hugo-module)

## References

- [https://gohugo.io/](https://gohugo.io/)
  - [https://gohugo.io/getting-started/](https://gohugo.io/getting-started/)
  - [https://gohugo.io/documentation/](https://gohugo.io/documentation/)
  - [https://themes.gohugo.io/](https://themes.gohugo.io/)
- [https://github.com/gohugoio/hugo](https://github.com/gohugoio/hugo)

Google: 'hugo dollar sign'

- [https://discourse.gohugo.io/t/the-dot-and-the-dollar-in-context/48604](https://discourse.gohugo.io/t/the-dot-and-the-dollar-in-context/48604)
  - [A Crash Course on Go Templates](https://www.youtube.com/watch?v=k5wJv4XO7a0)
  - [Golang documentation for the `text/template` package](https://pkg.go.dev/text/template)

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

## Quick start

Ref: [https://gohugo.io/getting-started/quick-start/](https://gohugo.io/getting-started/quick-start/)

```
$ hugo new site quickstart
Congratulations! Your new Hugo site was created in /tmp/quickstart.

Just a few more steps...

1. Change the current directory to /tmp/quickstart.
2. Create or install a theme:
   - Create a new theme with the command "hugo new theme <THEMENAME>"
   - Or, install a theme from https://themes.gohugo.io/
3. Edit hugo.toml, setting the "theme" property to the theme name.
4. Create new content with the command "hugo new content <SECTIONNAME>/<FILENAME>.<FORMAT>".
5. Start the embedded web server with the command "hugo server --buildDrafts".

See documentation at https://gohugo.io/.

$ cd quickstart

$ find . -type f | sort
./archetypes/default.md
./hugo.toml

$ cat archetypes/default.md
+++
date = '{{ .Date }}'
draft = true
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
+++

$ cat hugo.toml
baseURL = 'https://example.org/'
languageCode = 'en-us'
title = 'My New Hugo Site'
```
**Option 1**: follow `hugo new site quickstart` instructions to use `hugo new theme <THEMENAME>`:
```
$ hugo new theme barebone
Creating new theme in /tmp/quickstart/themes/barebone

$ echo "theme = 'barebone'" >> hugo.toml

$ hugo server
```
**Option 2**: follow [https://gohugo.io/getting-started/quick-start/](https://gohugo.io/getting-started/quick-start/) instructions:
```
$ git init

$ git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke

$ echo "theme = 'ananke'" >> hugo.toml

$ hugo server
```

### Add content

```
$ hugo new content content/posts/my-first-post.md
Content "/tmp/quickstart/content/posts/my-first-post.md" created

$ cat content/posts/my-first-post.md
+++
date = '2025-07-26T17:15:47Z'
draft = true
title = 'My First Post'
+++

$ vi content/posts/my-first-post.md

$ cat content/posts/my-first-post.md
+++
date = '2025-07-26T17:15:47Z'
draft = true
title = 'My First Post'
+++
## Introduction

This is **bold** text, and this is *emphasized* text.

Visit the [Hugo](https://gohugo.io) website!

$ hugo server -D
```

### Publish

As stated at [https://gohugo.io/getting-started/usage/](https://gohugo.io/getting-started/usage/):

- Hugo does not clear the public directory before building your site. Existing files are overwritten, but not deleted. This behavior is intentional to prevent the inadvertent removal of files that you may have added to the public directory after the build.
- Depending on your needs, you may wish to manually clear the contents of the public directory before every build.

With that information:

```
$ rm -rf public
$ hugo
```

## Themes

Ref: [https://github.com/halogenica/beautifulhugo](https://github.com/halogenica/beautifulhugo)

### Git submodule

```
$ git submodule add https://github.com/halogenica/beautifulhugo.git themes/beautifulhugo

$ echo "theme = 'beautifulhugo'" >> hugo.toml
```

### Hugo module

```
$ hugo mod init github.com/sfmunoz/hugo-playground

$ cat go.mod
module github.com/sfmunoz/hugo-playground

go 1.24.5

$ hugo mod get github.com/halogenica/beautifulhugo

$ cat go.mod
module github.com/sfmunoz/hugo-playground

go 1.24.5

require github.com/halogenica/beautifulhugo v0.0.0-20250508050025-e69e25d4ca0d // indirect

$ cat go.sum
github.com/halogenica/beautifulhugo v0.0.0-20250508050025-e69e25d4ca0d h1:H3Gf3B7nxMscrz+v7fn+PavLMUR+vCpcRJpzCAZy57A=
github.com/halogenica/beautifulhugo v0.0.0-20250508050025-e69e25d4ca0d/go.mod h1:4dwHt6njigk+fr9W3Bg+OflL4LKzkjbXAULXvr3mYLs=

$ cat >> hugo.html << __EOF
[[module.imports]]
  path = "github.com/halogenica/beautifulhugo"
__EOF
```
