# Flyttet til [Direktoratet for e-helse](https://github.com/Direktoratet-for-e-helse/Malarkitektur-digital-hjemmeoppfolging)

# Testdokumentasjon Målarkitektur-digital-hjemmeoppfølging

Testprosjekt for å se hvordan arkitekturdokumentasjon enklest mulig kan publiseres og vedlikeholdes på Github.
* [Generert dokumentasjon](https://thomiz.github.io/Malarkitektur-digital-hjemmeoppfolging/)

## Bruker 
* [just the docs - layout template for Github.io sidene](https://github.com/just-the-docs/just-the-docs)
* [Oversette](https://metamug.com/util/confluence-to-markdown/) confluence sider til markdown

## Forutsetninger (just-the-docs)

* index.md må ligge i rotkatalog på prosjektet?
* markdown filene bør ha just-the-docs metadata
~~~ 
---
layout: default
title: Innledning
nav_order: 1
---
~~~

## Testing med Read-the-docs og mkdocs

* Kjøre med peaceiris script og gh-pages build action
* Se på hvordan mkdoc themes kan enkelt tilpasses https://squidfunk.github.io/mkdocs-material/setup/changing-the-colors/
* Missing nav bar footer?
* Hvordan kjører vi versjoner
