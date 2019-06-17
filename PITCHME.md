## VueJS (vs Matestack)

---

@snap[north span-40]
## Inhalt
@snapend

@snap[west span-40 text-center]

Lernkurve
Code Style
Single File Components
Performance
Flexibilität

@snapend

@snap[east span-40 text-center]

Mobile
Community
Maturity
Support

@snapend

---

## Lernkurve

Bewährte Konzepte wurden von React und Angular angeeignet
Für Entwickler mit Erfahrungen in React oder Angular dadurch schnell erlernbar

+++

## Lernkurve

Gute Dokumentation
Doku ist klarer definiert als bei React
Viele Fragen lassen sich anhand der Doku schnell beantworten

---
## Code Style

Mix aus funktionaler und objektorientierter Programmierung
separiert HTML, JS und CSS. 
Bietet auch JSX-Style an
Komponenten-Lifecycle ist klar und intuitiv

---
## Single File Components

Single File Components sind in 3 Bereiche separiert:
```javascript
<template>, <script> und <style>
```

jeder Bereich enthält den entsprechenden Code-Type

+++

### <template>

@snap[west span-40 text-center]
 hllo
@snapend

@snap[east span-40 text-center]
pug Templates analog zu slim
Two-Way Data Binding
@snapend

+++

### <script>
@snap[west span-40 text-center]
```
@snapend

@snap[east span-40 text-center]


@snapend


+++

@snap[north span-40 text-center]
## <style>
@snapend

@snap[west span-40 text-center]
```
<style>
```
@snapend

@snap[east span-40 text-center]
Im Style der Komponente wird das CSS hinterlegt
durch ``` <style lang="scss"> ``` kann man  
@snapend

---

@snap[west span-40 text-center]
## Performance

Größe der Vue-Bibliothek: 31KB
@snapend

@snap[east span-40 text-center]
![Performance](assets/img/performance.png)
@snapend

---
## Flexibilität

* In der Core Bibliothek von Vue sind die fundamentalen Features um eine App zu bauen integriert.
* Darüber hinaus gibt es einige Erweiterungen, die einfach installiert sind z.B.
  * Vuex für das State-Management
  * Vue Router für das URL-Management innerhalb der App
  * Vue Server-Side Renderer
---

## Mobile

* es gibt mehrere Optionen um Native Apps mit Vue zu bauen. Es gibt jedoch keinen klaren Marktführer.
* NativeScript, Weex und Quasar sind da zu nennen
---
## Community

* Bei Stackoverflow gibt es ~37000 tags mit #vue (React: ~144.000)
* Es gibt ~15.500 npm Pakete bereit zum Installieren (React: ~41.000)
* Bei Github hat das Vue Repository ~142.000 Sterne (React: ~131.000)
* Die meisten Probleme werden bereits in der Dokumentation beantwortet

---
## Wie erwachsen ist VueJs

* Vue wurde im Feburar 2014 released
* Vue wird laut SimiliarTech von ~75.000 Domains verwendet (React: ~263.000)
* Vue wird unter anderem von folgenden Unternehmen verwendet:
  * 9GAG
  * Gitlab
  * Grammarly
  * Nintendo
---
## Support

* Vue ist eine unabhängige Bibliothek
* Das Vue-Team hat 23 Entwickler
* Die Vue Roadmap kann im Github-Repository eingesehen werden

---
## Zusammenfassung

---
## Pros

* Vue's Kernmodule (Vuex, Router, usw.) sind integriert und funktionieren sehr gut
* Schnelle Einarbeitung
* FEDs und BEDs können sich gut und schnell zurechtfinden

---
## Cons

* weniger Plugins und Tools als bei React oder Angular
* kleinere Community

---
## Single File Components

+++
Components können genutzt werden um gekapselte Funktionalitäten zu erstellen 

+++
Components können in andere Components geladen werden und verhalten sich wie Partials

+++
Mit Vue Router können Seitenaufrufe gehandelt werden

+++
```
router-view
```
ermöglicht es die Components zu rendern.
+++
Im route.js werden die Routes deklariert
```
export const routes = [
  { path: '/dashboard', component: Dashboard, children: [
    { path: '/dashboard/posts/index', component: Posts },
  ]},
];
```

+++
Die Child-Component Posts wird im Dashboard mit 
```
router-view
```
wiederum geladen
+++
Es kann mehrere Child-Components geben. Diese können wiederum Child-Components besitzen
+++
Um den State einer App handhaben zu können, wird Vuex genutzt
 
---