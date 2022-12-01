# Flyttet til [Direktoratet for e-helse](https://github.com/Direktoratet-for-e-helse/Malarkitektur-digital-hjemmeoppfolging)

# Testdokumentasjon Målarkitektur-digital-hjemmeoppfølging

Testprosjekt for å se hvordan arkitekturdokumentasjon enklest mulig kan publiseres og vedlikeholdes på Github.
* [Generert dokumentasjon](https://thomiz.github.io/Malarkitektur-digital-hjemmeoppfolging/)

## Tema

* Kjøre med peaceiris script og gh-pages build action
* Se på hvordan Mkdoc themes kan enkelt tilpasses https://squidfunk.github.io/mkdocs-material/setup/changing-the-colors/
* [Material](https://squidfunk.github.io/mkdocs-material/reference/)

### Mangler

* Mangler nav bar footer?
* Mangler fargerike labels

### Brukte tema (historikk)

* [just the docs - layout template for Github.io sidene](https://github.com/just-the-docs/just-the-docs)
* [Oversette](https://metamug.com/util/confluence-to-markdown/) confluence sider til markdown

## Forutsetninger (just-the-docs)

* index.md må ligge i rotkatalog på prosjektet?
* markdown filene bør ha just-the-docs metadata

~~~yaml
---
layout: default
title: Innledning
nav_order: 1
---
~~~

## Testing med Read-the-docs, mkdocs og just the docs (ghpages)

* Hvordan kjører vi versjoner ([mike](https://github.com/jimporter/mike))

* Prøvde dette scriptet for å bruke just the docs temaet med push til gh-branchen, men det feilet når Jekyll skulle startes
  * [Jekyll med just-the-docs](https://github.com/MichaelCurrin/jekyll-actions-quickstart)
