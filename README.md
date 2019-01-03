# Welcome to the Dropsource community hub repo

This is the source code for [community.dropsource.com](https://community.dropsource.com). The site is built using [Jekyll](https://jekyllrb.com/) and [GitHub Pages](https://pages.github.com/). Check out the [contributing guide](CONTRIBUTING.md) if you'd like to report an issue with the community hub site or get involved with the repo in any other way!

## Site implementation

The community hub is essentially a one page site. Most of the content in that page is in [index.md](index.md), but it also uses a few [includes](_includes) for the feeds from other sources (the Dropsource Discourse forum, GitHub, Medium, and Trello). Those are the main files for site content (in markdown and HTML), with a [Sass](_sass) file for styling. The site layout and style use the [Cayman theme](https://pages-themes.github.io/cayman/) with a few minor modifications.