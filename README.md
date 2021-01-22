# govuk-hugo

`govuk-hugo` is a theme for the Hugo static site builder that is based on the [GOV.UK Design System](https://design-system.service.gov.uk/).

[Hugo](https://gohugo.io/) is a lightweight static site builder.

This is a work in progress. It has been created to help Cabinet Office Analysts make simple public facing sites for official statistics and open source works using the GOV.UK design system. In addition to the design system, as a data team, it has been inspired by Public Health England's [Coronavirus data dashboard](https://coronavirus.data.gov.uk/), which has adapted the GOV.UK style for data visualisation.

## Installation

Follow Hugo's instructions on [getting started](https://gohugo.io/getting-started/).

To install the theme either:

Download this repo as a zip and extract the files and copy them to the folder `themes/govukhugo` within your Hugo site base folder (note the lack of dash!!).

Or, add `govuk-hugo` as a submodule to your Hugo site's repository

```
$ git submodule add https://github.com/co-analysis/govuk-hugo.git themes/govukhugo
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
  logotext: TST
  product: Test Site
  phase: alpha
  feedbackurl: https://github.com/mattkerlogue/hugo-test/issues/

```

If deploying to GitHub Pages you must set `publishDir: docs` and `canonifyurls: true`.

Set `unsafe: true` if you want to be able to use raw HTML in in markdown documents.

Unless you are deploying to a .gov.uk subdomain you should set `govuk:false` - this ensures you do not use GOV.UK's _New Transport_ font, nor use the GOV.UK crown in the header and as the favicon.

You should provide a service acronym using `logotest: ABC` - this should be capitalised. If deploying to service.gov.uk you should set this as `logotest: GOV.UK`.

You can provide a product name using `product: Product Name` which will provide the product name in the header. If a product name is not provided the `title` specified at the top of the config.yaml file will be used.

To add a GOV.UK style "phase" banner set `phase: alpha` or `phase:beta` in the params. You should also provide a feedback URL using `feedbackurl: https://your.site/feedback`
