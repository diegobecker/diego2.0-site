# Diego Becker — Personal Website

Personal website and blog built with [Hugo](https://gohugo.io/) and [PaperMod](https://github.com/adityatelange/hugo-PaperMod).

## Requirements

- Hugo Extended 0.147.7
- [mise](https://mise.jdx.dev/)

The Hugo version is pinned in `mise.toml`.

## Development

Install the project dependencies:

```bash
mise install
```

## Start the local development server:

```bash
hugo server -D
```

## The site will be available at:

```bash
http://localhost:1313/
```

## Build

### Build the production site locally:

```
hugo --minify
```

### Content

Posts are available in Portuguese and English.

Content is organized by language:

```
content/
├── pt/
│   └── posts/
└── en/
    └── posts/
```

## Theme

The site uses PaperMod as a Git submodule:

```
git submodule update --init --recursive
```