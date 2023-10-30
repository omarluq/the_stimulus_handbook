---
theme: dracula
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Stimulus JS
drawings:
  persist: false
transition: slide-left
title: Stimulus JS
mdc: true
---
<div class='flex flex-col gap-3 content-center'>
  <img src="/stimulus-logo.svg" class="rounded shadow h-60" />
  <h1> Stimulus Js </h1>
</div>

---
transition: slide-left
---
<h1> What is StimulusJS </h1>
<v-clicks>
<p> Stimulus is a lightweight and minimalistic JavaScript framework. Instead of focusing on HTML rendering, it boosts your current HTML elements by leveraging data attributes. </p>

<div class='pb-2'><span style="color: #007bff;">💡</span> <strong>Flexibility:</strong> Unlike many other frameworks that come with a heavy set of rules and structures, Stimulus takes a more flexible approach.</div>
<div class='pb-2'><span style="color: #28a745;">🌐</span> <strong>HTML Enhancement:</strong> Its basic concept is to enhance existing HTML. Instead of requiring developers to rewrite or replace their HTML, Stimulus augments it, tapping into the power of data attributes.</div>
<div class='pb-2'><span style="color: #dc3545;">🔗</span> <strong>Harmonious Integration:</strong> This design promotes a harmonious blend of JavaScript's dynamic capabilities with the foundational structure of web content.</div>
<div>
<div class='flex flex-row gap-5 pt-1'>
```js
import { Controller } from 'stimulus'

export default class GreeterController extends Controller {
  // ...
}
```
```html
<div data-controller='greeter'></div>
```
</div>
</div>
</v-clicks>

---
transition: slide-left
---
<h1>Controllers in StimulusJS</h1>
<v-clicks>
<p>Controllers are at the heart of StimulusJS, acting as the primary means of adding behavior to HTML elements.</p>
<div class='pb-2'>
  <span style="font-weight: bold; color: #007bff;">&#9679; Connection to HTML:</span> Controllers are JavaScript classes that connect to HTML elements via data attributes.
</div>
<div class='pb-2'>      
  <span style="font-weight: bold; color: #28a745;">&#9679; Lifecycle:</span> Each controller has lifecycle callbacks like <code>connect()</code> and <code>disconnect()</code>, allowing you to set up and tear down your JavaScript code in an organized way.
</div>
<div class='pb-2'>      
  <span style="font-weight: bold; color: #dc3545;">&#9679; Reusability:</span> Controllers can be reused across your application, leading to more maintainable and module code.
</div>
<div class='flex flex-row gap-5 pt-1'>
```js
import { Controller } from 'stimulus'

export default class GreeterController extends Controller {
  connect() {
    console.log('Hello World!');
  }

  disconnect() {
    console.log('Goodbye World!');
  }
}
```
```html
<div data-controller='greeter'></div>
```
</div>
</v-clicks>
---
transition: slide-left
---
<h1>StimulusJS Blessings</h1>
<v-clicks>
<p> 
  In the world of StimulusJS, <em>blessings</em> refer to a suite of refined features and patterns that enhance the developer experience. These blessings are essentially pre-defined behaviors or functionalities that you can easily apply to your HTML elements, streamlining the process of creating interactive and dynamic web interfaces. They encapsulate common tasks and behaviors, making your code more concise, readable, and maintainable. As of Stimulus 3.2, the Controller class's blessings are:
</p>  
<h2 class='pb-3'>StimulusJS Blessings:</h2>
<div class='pb-1'><strong>🎨 ClassPropertiesBlessing:</strong> Enables easy manipulation and observation of CSS classes on controller elements.</div>
<div class='pb-1'><strong>🎯 TargetPropertiesBlessing:</strong> Facilitates the referencing and management of DOM elements as targets within the controller.</div>
<div class='pb-1'><strong>🔢 ValuePropertiesBlessing:</strong> Simplifies handling of state and data by binding values to controller elements.</div>
<div class='pb-1'><strong>🔌 OutletPropertiesBlessing:</strong> Allows for enhanced organization of related DOM elements, streamlining complex element interactions.</div>
</v-clicks>
---
transition: slide-left
---
<h1>ClassPropertiesBlessing</h1>
<v-clicks>
<p><code>ClassPropertiesBlessing</code> allows you to define a structured list of CSS class names within your controller. This helps in maintaining a clear connection between your JavaScript and CSS. While it doesn't automatically manage class states based on property changes, it provides a declarative way to handle class names, improving code readability and organization.</p>

<div class='flex flex-row gap-5'>
```js
import { Controller } from "stimulus"

export default class ToggleController extends Controller {
  static classes = ["active"]

  connect() {
    setInterval(() => {
      this.element.classList.toggle(this.activeClass)
    }, 10000); // Toggles class every 10 seconds
  }
}
```
```html
<div data-controller="toggle" 
      data-toggle-active-class="highlight">
  Toggle Element
</div>

<style>
  .highlight {
    color: blue;
    font-weight: bold;
  }
</style>
```
</div>
</v-clicks>

---
transition: slide-left
---
<h1>TargetPropertiesBlessing</h1>
<v-clicks>
<!-- <p>The <code>TargetPropertiesBlessing</code>, or simply <code>Targets</code>, enhances your controller by allowing direct references to specific DOM elements and lifecycle callbacks for those elements. By defining targets, you avoid complex query selectors and ensure a clean separation between your JavaScript and HTML structure. This feature is a cornerstone of Stimulus, promoting clear communication between your controller and its associated elements.</p> -->
<p>The <code>TargetPropertiesBlessing</code>, or simply <code>Targets</code>, enhances your controller by allowing direct references to specific DOM elements. By defining targets, you avoid complex query selectors and ensure a clean separation between your JavaScript and HTML structure. Moreover, Stimulus provides lifecycle callbacks for each target, giving you precise control over their behavior as they are added to or removed from the DOM.</p>
<div class='flex flex-row gap-5'>
```js
import { Controller } from "stimulus"

export default class ToggleController extends Controller {
  static classes = ["active"]
  static targets = ["toggleElement"]

  toggleElementTargetConnected(element) {
    this.interval = setInterval(() => {
      this.toggleElementTarget.classList.toggle(this.activeClass)
    }, 10000); // Toggles class every 10 seconds
  }

  toggleElementTargetDisconnected(element) {
    clearInterval(this.interval);
  }
}
```
```html
<div data-controller="toggle">
  <div data-toggle-target="toggleElement">
    Toggle Element
  </div>
</div>

<style>
  .highlight {
    color: blue;
    font-weight: bold;
  }
</style>
```
</div>
</v-clicks>

---
transition: slide-left
---