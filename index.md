# Hochschule Mannheim - Das clientseitige JavaScript-Webframework Vue.js
__Original Datei mit aktiven Links: [https://github.com/lehnert-andre/hs-mannheim-vue-js/blob/master/index.md](https://github.com/lehnert-andre/hs-mannheim-vue-js/blob/master/index.md)__

Zusammenfassung des Gastvortrags

## Vorstellung

  - eXXcellent solutions
    https://www.exxcellent.de/
  - Coworking Space in Mannheim
    https://bauteilb.de/
  - Praktika, Abschlussarbeiten und Werkstudenten-Tätigkeiten
    https://www.exxcellent.de/karriere/praktika-abschlussarbeiten/
    
## Folien

- Folien (Web): https://slides.com/andre-lehnert/hs-mannheim-vue-js/fullscreen

## Live-Demo

- Web-App: https://kitten-experience.web.app/
- Repository mit dem Code: https://github.com/lehnert-andre/kitten-experience

## Einführung in Vue.js

- Lesson 1: https://stackblitz.com/edit/vue-js-lesson-01 / https://stackblitz.com/edit/vue-js-lesson-01-solution
- Lesson 2: https://stackblitz.com/edit/vue-js-lesson-02 / https://stackblitz.com/edit/vue-js-lesson-02-solution
- Lesson 3: https://stackblitz.com/edit/vue-js-lesson-03 / https://stackblitz.com/edit/vue-js-lesson-03-solution

### Vue.js Komponenten

Komponenten werden in Vue.js analog zur App als JSON definiert und sind bis auf die el-Property identisch.
Es gibt zwei Arten zur Registrierung von Komponenten. Die globale Registrierung per Vue.component('komponenten-name', {...}) oder lokal per Variable mit dem JSON. Bei der globalen Variante, können alle Komponenten ohne weitere Konfiguration alle anderen Komponenten nutzen. Bei der lokalen Variante wird die Nutzung der Komponente explizit über die components-Property definert.

Siehe https://vuejs.org/v2/guide/components.html

### Deklarativer Rendering-Mechanismus

Der deklarative Rendering-Mechanismus von Vue erlaubt eine dynamische Manipulation des DOM-Baums. Vue nutzt ein HTML-Template, erstellt einen virtuellen DOM-Baum, ersetzt Platzhalter und bindet Properties ein. Der virtuelle DOM-Baum wird anschließend in den DOM-Baum des Browsers übertragen.

#### Text Interpolation

Ein Platzhalter im Template {{Name der referenzierten Property}} erlaubt eine reaktive Verknüpfung von Werten der data- oder computed-Properties. Der Syntax entspricht der {{Mustache}}-Syntax.

Über die Console des Browsers app.name = 'Manuelle Eingabe' eingeben, um den Wert der name-Property zu ändern.

Siehe https://vuejs.org/v2/guide/syntax.html

#### v-bind

Vue erlaubt ebenfalls eine lesende Verknüpfung von Properties mit HTML-Attributen. Der {{Mustache}}-Syntax kann nicht genutzt werden. Daher wird eine sogenannte Direktive (directive) innerhalb des HTML-Elements genutzt. Bei Vue beginnen Direktiven mit dem Präfix v-.

Zum "Binden" von Properies mit HTML-Attributen wird v-bind: genutzt. Der Zugriff auf die Properties erfolgt dabei unidirektional und lesend.

Beispiel:
```
<a v-bind:href="link" v-bind:title="linkTitle">{{linkText}}</a>
```
Alternativ kann auch einfach ein : statt v-bind: verwendet werden.
Siehe https://vuejs.org/v2/guide/syntax.html#Arguments

#### v-model

Die v-model Direktive erlaubt ein bidirektionales "Binden" von Vue-Properties. Neben dem lesenden Zugriff werden hier auch Änderungen (schreibender Zugriff) an den Properties möglich. Vue im Hintergrund einen Event-Listener, der bei Änderungen den neuen Property-Wert übernimmt.

Beispiel:
```
<input v-model:value="name" />
```
Änderungen am value des Input-Elements werden automatisch in die Vue-Property name geschrieben.

Siehe https://vuejs.org/v2/guide/forms.html

#### v-for
Zur Darstellung von Listen bietet Vue die v-for-Direktive zum Iterieren über Array-Elemente an. Die Funktionsweise entspricht einer for-Schleife.

Beispiel:
```
<ol>
  <li v-for="todo in todos">
    {{ todo.text }}
  </li>
</ol>
...
data: {
  todos: [
    { text: 'Learn JavaScript' },
    { text: 'Learn Vue' },
    { text: 'Build something awesome' }
  ]
}
```
Siehe https://vuejs.org/v2/guide/list.html

#### v-if, v-else und v-else-if
Zur Darstellung bestimmter HTML-Elemente bietet Vue die v-if-Direktive an, um bestimmte boolsche Konditionen abzufragen. Die Funktionsweise entspricht einer if-Bedingung.
Zur if-Bedingung gehören auch der else-Fall (v-else) und die weitere Konditionsprüfungs mittels else if (v-else-if).

Beispiel:
```
<p v-if="animal === '🐶'" >Dog</p>
<p v-else-if="animal === '🐱'" >Cat</p>
<p v-else>Unknown</p>
...
data: {
  animal: '🐶'
}
```

Siehe https://vuejs.org/v2/guide/conditional.html

#### Das &lt;template&gt;-Element
  
Das &lt;template&gt;-Element ist ein Hilfsmittel für das Rendering von v-for- und v-if-Blöcken, die mehr als ein HTML-Element enthalten oder später im DOM nicht mehr sichtbar sein sollen.

#### Computed Properties

Der deklarative Rendering-Mechanismus von Vue erlaubt innerhalb des Platzhalters auch JavaScript-Logik. Falls diese Logik zu kompliziert wird, bieten sich computed-Properties an. Diese werden als Funktion innerhalb des computed-Blocks definert und bieten in der Regel nur einen lesenden Zugriff (Getter).

Siehe https://vuejs.org/v2/guide/computed.html#Computed-Properties

#### Event Handling

Vue.js bietet mit der v-on-Direktive eine einfache Möglichkeit an auf DOM Events zu reagieren. v-on:click ist ein typisches Beispiel, um auf OnClick-Events zu reagieren. Die Direktive kann den JavaScript-Code direkt ausführen, z.B. v-on:click="counter += 1" oder ruft eine Function im methods-Vue-Block auf.
Die v-on:-Direktive kann mit @ abgekürzt werden.

Siehe https://vuejs.org/v2/guide/events.html

## Vuex – Ein Store bringt Ordnung in großen Anwendungen

- Vuex: https://vuex.vuejs.org/
- Vuex Einführungsvideo: www.vuemastery.com/courses/mastering-vuex/intro-to-vuex/
- Vuex Beispiel aus der "kitten-experience" App: https://github.com/lehnert-andre/kitten-experience/blob/feature/simple-example/frontend/kitten-experience/store/KITTEN.js

## Abschluss

- Mentimeter Abstimmung
  https://www.mentimeter.com/s/3416034713636eecbc321e1a712c3377/4f8e5b45f784
