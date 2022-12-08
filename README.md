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

### Oppdatere Just-the-docs versjon samtidig som mkdocs

* ~~Just-the-docs kan bare eksistere i hovedkatalogen på gh-pages branchen på github.io, ellers brytes alle koblinger til bilder og andre sider (kanskje det eksisterer en innstilling?)~~
* Mkdocs versjonen kan godt ligge under katalog (for eksempel "currentbuild") uten at lenker brytes
* Scriptet fungerer for produksjon av just-the-docs og deploy til gh-pages branch (root) *Deploy Jekyll with JTD to gh-pages(root)*
  * Scriptet sletter gh-pages branchen i sin helhet før ny deploy
  * Det er peaciris action som sletter også currentbranch katalogen
    * Løsning, enten bruke opsjon for å beholde filer eller legge byggene i underkataloger, peaciris sletter bare gjeldende deploykatalog i destination_dir (men hvis dette er rotkatalogen (".") slettes hele gh-pages branchen)

### Konfigurere Just-the-docs for eksistens i underkatalog (e.g. currentbuild)

Konfigurere baseurl og hostname for hvor dokumentasjonen skal ligge i _config.yml
~~~yaml
baseurl: "/Malarkitektur-digital-hjemmeoppfolging/JTD-currentbuild" # the subpath of your site, e.g. /blog
url: "https://thomiz.github.io" # the base hostname & protocol for your site, e.g. http://example.com
~~~

Konfigurere deployscriptet tilsvarende (hvor peaciris legger produsert dokumentasjon).
~~~yaml
- name: Deploy
    uses: peaceiris/actions-gh-pages@v3
    with:
      github_token: ${{ secrets.GITHUB_TOKEN }}
      publish_dir: ./_site
      destination_dir: ./JTD-currentbuild # Må stemme med baseurl: parameter i _config
~~~