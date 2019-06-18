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
Matestack

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

### template
```
<template lang="pug">
#app
  template(v-for="item in items")
    v-img(:src='item.image', height='200px')
      .headline {{ item.count }} {{ item.headline }}
        span.grey--text {{ item.subHeadline }}
</template>
```

pug Templates analog zu slim  
Two-Way Data Binding

+++
### script

```javascript
<script>
export default {
  data: function () {
    return {
      items: [ {
          image: 'url', 
          headline: 'headline', 
          subheadline: 'subheadline', 
          count: 5 
        }
      ]
    }
  },
  components: {
  },
  created(){
  },
  methods: {
  }
}
</script>
```

+++

## style

```
<style>
```

Im Style der Komponente wird das CSS hinterlegt
durch ``` <style lang="scss"> ``` kann eine beliebige Stylesheet-Sprache ausgewählt werden  

---

@snap[west span-60 text-center]
## Performance

Größe der Vue-Bibliothek: 31KB
@snapend

@snap[east span-40 text-center]
![Performance](assets/img/performance.png)
@snapend

---

## Flexibilität

Im Core sind die wichtigsten Bestandteile bereits integriert  
Darüber hinaus gibt es einige sinnvolle Erweiterungen

+++
### Vuex für das State-Management
Es gibt einen zentralen Store  
in diesem wird der Zustand der Anwendung gespeichert
```javascript
const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    }
  }
})
```
+++
### Vue Router für das URL-Management

```javascript
import Posts from '../components/posts/index.vue'

export const routes = [
  { path: '/posts', component: Posts }
```

+++

### Vue Router für das URL-Management

```
router-link(to="/posts")
  | Index
router-view
```

Beim Klick auf Index wird dann die Komponente Posts in router-view gerendered

---

## Mobile

Mehrere Optionen Native Apps zu erstellen:
Nativescript, Weex und Quasar 

---
## Community

wachsende Zahlen

+++

### Github Stars History

![Github](assets/img/github.png)

+++

### Stackoverflow-Tags History

![Stackoverflow](assets/img/stackoverflow.png) 

+++

### NPM Packages

![NPM](assets/img/npm.jpeg)

---
## VueJS Production Ready?

Vue wurde im Feburar 2014 released
und wird laut SimiliarTech von ~75.000 unique Domains verwendet (React: ~263.000)

+++

## VueJS Production Ready?
Vue wird unter anderem von folgenden Unternehmen verwendet:

@ul
- 9GAG  
- Gitlab  
- Grammarly  
- Nintendo  
@ulend
---

## Support

23 Entwickler im Vue Team
Roadmap für nächste Versionen kann im Github-Repository eingesehen werden

---
## Zusammenfassung

---
## Pros

* Vue's Kernmodule funktionieren sehr gut
* Dokumentation
* Data Binding
* Schnelle Einarbeitung
* FEDs und BEDs können sich gut und schnell zurechtfinden

---
## Cons

* weniger Plugins und Tools als bei React
* kleinere Community

---

## Matestack

VueJS in Ruby Code

+++
### SPA

```ruby
class Apps::MyApp < App::Cell::App
  def response
    components{
      header do
        heading size: 1, text: "My App"
      end
      nav do
        transition path: :my_first_page_path do
          button text: "Page 1"
        end
        transition path: :my_second_page_path do
          button text: "Page 2"
        end
      end
      main do
        page_content #pages are dynamically yielded here, when buttons are clicked!
      end
      footer do
        plain "That's it!"
      end
    }
  end
end
```
+++

### Components

```ruby 
class Pages::MyApp::MyFirstPage < Page::Cell::Page
  def response
    components{
      div id: "div-on-page-1" do
        plain "My First Page"
      end
    }
  end
end
```
+++
### Pros

- ruby
- Datenaustausch zwischen Backend und Frontend sehr einfach
- Cells
- Kommunikation mit Matestack-Entwicklern über Gitter 

+++

### Cons

- noch nicht möglich VueJS 'Gems' einzubinden
- es können keine child Components gerenderd werden
- Webpacker-Integration fehlt noch
- bisher nur für kleine und einfache Anwendungen sinnvoll

+++
### Matestack View Method

```ruby
def response
  components {
    div class: 'row' do
      div class: "offset-md-4"
      div class: "col-md-4" do
        div class: "card", id: "post-card" do
          img class: "card-img-top", path: 'posts.jpg'
          div class: "card-body" do
            heading size: 4, class: "card-title", text: post.title
            div class: "card-text" do
              plain post.text
            end
            br
            div class: 'row' do
              div class: "col-md-3" do
                onclick emit: "display_comments" do
                  div class: "card-text post-card-comments" do
                    plain "#{comments.count} Kommentare"
                  end
                end
              end
              div class: "col-md-9" do
                onclick emit: "create_comment" do
                  div class: "card-text post-card-create-comment" do
                    plain "Kommentar erstellen"
                  end
                end
              end
            end
            div class: "post-card-bottem-right-created-at" do
              plain timeago_tag post.created_at, format: "%d.%m.%Y"
            end
          end
        end
      end
    end
    div class: 'row' do
      div class: "offset-md-4"
      div class: "col-md-4" do
        async show_on: "display_comments" do
          comments.each do |c|
            partial :comment_item, c
          end
        end
      end
    end
    div class: 'row' do
      div class: "offset-md-4"
      div class: "col-md-4" do
        async show_on: "create_comment" do
            partial :create_comment
          end
        end
      end
    end
  end
  # sub-components funktionieren noch nicht mit 0.6 erst mit 0.7
```

+++ 
### VueJS template mit Pug
```
<template lang="pug">
#app
  v-layout(row='', wrap='')
    v-flex(xs12='', sm6='', offset-sm3='')
      v-card
        v-img(src='https://picsum.photos/500', height='200px')
        v-card-title(primary-title='')
          div
            .headline {{ post.title }}
            span.grey--text {{ post.text }}
        v-card-actions
          v-btn(flat='', color='purple', @click="comments = !comments") 
            | {{ post.comments.length }} Kommentare
          v-spacer
      div(v-if="comments")
        template(v-for="(comment, index) in post.comments")
          comment-show(:key="comment.id", :text="comment.text", :name="comment.name", :createdAt="comment.createdAt")
          template(v-if="index == post.comments.length - 1")
            comment-create(:postId="id", @commentCreated="setCommentToPost")
</template>
```