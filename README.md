# govukhugo

**BREAKING CHANGE**: The repository is now named **govukhugo** (formerly govuk-hugo).

`govukhugo` is a theme for the Hugo static site builder that is based on the [GOV.UK Design System](https://design-system.service.gov.uk/).

[Hugo](https://gohugo.io/) is a lightweight static site builder.

This is a work in progress. It has been created to help Cabinet Office Analysts make simple public facing sites for official statistics and open source works using the GOV.UK design system. In addition to the design system, as a data team, it has been inspired by Public Health England's [Coronavirus data dashboard](https://coronavirus.data.gov.uk/), which has adapted the GOV.UK style for data visualisation.

## Features

`govukhugo` uses [GOV.UK Frontend v3.10.2](https://github.com/alphagov/govuk-frontend/releases/tag/v3.10.2).

Hugo uses [Goldmark](https://github.com/yuin/goldmark/) to render markdown to HTML. While boilerplate elements (the header, footer and navbar structure) are natively written to support the Design System, Goldmark does not add the Design System classes to the rendered HTML, the footer content includes JavaScript that applies the Design System CSS to relevant HTML tags. Therefore, `govukhugo` is not suitable for environments that do not support JavaScript.

`govukhugo` does not use SASS for CSS processing, therefore the `dashboard-layout.css` provides the GOV.UK colour palettes as `:root` variables.

`govukhugo` is designed for dashboards, and uses a wider maximum page width than standard GOV.UK pages. Text elements are however limited to a max-width to improve readability: `<p>` and `<pre>` elements are limited to 810px; `<li>` elements are limited to 700px). Other elements (e.g. tables, images, interactives).

`govukhugo` supports code blocks, and provides syntax highlighting with [Highlight.js](https://highlightjs.org/).

### Menu

`govukhugo` uses a sidebar menu, this relies on your content being organised within sections underneath the `content` folder. Your homepage will not show in the menu. If an `about.md` file is included in the `content` folder then this is rendered as an additional link at the bottom of the menu, any other files in the content directory but not within a sub-folder are not rendered.

## Installation

Follow Hugo's instructions on [getting started](https://gohugo.io/getting-started/).

To install the theme either:

Download this repo as a zip and extract the files and copy them to the folder `themes/govukhugo` within your Hugo site base folder (note the lack of dash!!).

Or, add `govukhugo` as a submodule to your Hugo site's repository

```
$ git submodule add https://github.com/co-analysis/govukhugo.git themes/govukhugo
```

## Configuration

To use this theme ensure your hugo `config.yaml` follows this example:

```
baseURL: https://your.site/
languageCode: en-gb
title: My Site Title
theme: govukhugo
publishDir: docs
canonifyurls: true

markup:
  goldmark:
    renderer:
      unsafe: true

params:
  govuk: false
  logotext: ABC
  product: Product Name
  phase: alpha
  feedbackurl: https://your.site/feedback/

```

If deploying to GitHub Pages you must set `publishDir: docs` and `canonifyurls: true`.

Set `unsafe: true` if you want to be able to use raw HTML in in markdown documents.

Unless you are deploying to a .gov.uk subdomain you should set `govuk:false` - this ensures you do not use GOV.UK's _New Transport_ font, nor use the GOV.UK crown in the header and as the favicon.

You should provide a service acronym using `logotest: ABC` - this should be capitalised. If deploying to service.gov.uk you should set this as `logotest: GOV.UK`.

You can provide a product name using `product: Product Name` which will provide the product name in the header. If a product name is not provided the `title` specified at the top of the config.yaml file will be used.

To add a GOV.UK style "phase" banner set `phase: alpha` or `phase:beta` in the params. You should also provide a feedback URL using `feedbackurl: https://your.site/feedback`
