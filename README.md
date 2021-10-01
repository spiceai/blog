# Spice.ai Blog

The Spice.ai blog at [blog.spiceai.org](https://blog.spiceai.org)

## Setup

```bash
brew install hugo
npm install -D autoprefixer
npm install -D postcss-cli
npm install -D postcss
git submodule init
git submodule update --init --recursive
npm install
```

- Hugo install reference: [gohugo.io/getting-started/installing/](https://gohugo.io/getting-started/installing/)
- Docsy install reference: [www.docsy.dev/docs/getting-started](https://www.docsy.dev/docs/getting-started)

## Build

```bash
hugo -D
```

## Run

```bash
hugo server -D
```
