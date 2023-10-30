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
  <img src="/stimulus-logo.svg" class="h-60" />
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
<h1>StimulusJS APIs</h1>
<v-clicks>
<p> 
In the realm of StimulusJS, there are a set of advanced features and patterns that significantly elevate the developer experience. These features, akin to APIs, offer pre-defined behaviors or functionalities that you can seamlessly integrate into your HTML elements. This streamlines the creation of interactive and dynamic web interfaces.
By encapsulating common tasks and behaviors, these APIs make your code not only more concise but also easier to read and maintain. As of Stimulus 3.2, the Controller class includes these notable APIs:
</p>  
<div class='pb-1'><strong>🎨 Classes API:</strong> Enables easy manipulation and observation of CSS classes on controller elements.</div>
<div class='pb-1'><strong>🎯 Targets API:</strong> Facilitates the referencing and management of DOM elements as targets within the controller.</div>
<div class='pb-1'><strong>🔢 Values API:</strong> Simplifies handling of state and data by binding values to controller elements.</div>
<div class='pb-1'><strong>🔌 Outlets API:</strong> Allows for enhanced organization of related DOM elements, streamlining complex element interactions.</div>
</v-clicks>
---
transition: slide-left
---
<h1>Classes API</h1>
<v-clicks>
<p><code>Classes API</code> allows you to define a structured list of CSS class names within your controller. This helps in maintaining a clear connection between your JavaScript and CSS. While it doesn't automatically manage class states based on property changes, it provides a declarative way to handle class names, improving code readability and organization.</p>

<div class='flex flex-row gap-5'>
```js
import { Controller } from "@hotwired/stimulus"

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
<h1>Targets API</h1>
<v-clicks>
<p>The <code>Targets API</code>, enhances your controller by allowing direct references to specific DOM elements. By defining targets, you avoid complex query selectors and ensure a clean separation between your JavaScript and HTML structure. Moreover, Stimulus provides lifecycle callbacks for each target, giving you precise control over their behavior as they are added to or removed from the DOM.</p>
<div class='flex flex-row gap-5 max-h-fit'>
```js
import { Controller } from "@hotwired/stimulus"

export default class ToggleController extends Controller {
  static classes = ["active"]
  static targets = ["toggleElement"]

  toggleElementTargetConnected(element) {
    this.interval = setInterval(() => {
      element.classList.toggle(this.activeClass)
    }, 10000); // Toggles class every 10 seconds
  }

  toggleElementTargetDisconnected(_element) {
    clearInterval(this.interval);
  }
}
```
```html
<div data-controller="toggle">
  <div data-toggle-target="toggleElement"
       data-toggle-active-class="highlight">
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
<h1>Values API</h1>
<v-clicks>
<div>The <code>Values API</code> in Stimulus powers up your controller with state management. This feature links HTML data attributes to JavaScript properties.</div>

<div class='py-2'>Value Properties:</div>
<div>🔹 <code>[name]Value</code>: Dynamic getter and setter for the value.</div>
<div>🔹 <code>has[name]Value</code>: Checks if the value is defined.</div>
<div>🔹 <code>[name]ValueChanged</code>: Callback fired when the value changes.</div>
<div class='py-2'>Strong Typing: Define the type of data your values should hold. Supported types:</div>
<div>   🚀 String: For text-based values.</div>
<div>   🚀 Number: For numerical values.</div>
<div>   🚀 Boolean: For true/false values.</div>
<div>   🚀 Array: To hold a list of items.</div>
<div>   🚀 Object: For structured data in JSON-like format.</div>
</v-clicks>

---
transition: slide-left
---
<h1>Values API Example</h1>
<div class='flex flex-row gap-5'>
```js
import { Controller } from "@hotwired/stimulus"

export default class TimerController extends Controller {
  static values = { seconds: Number }

  connect() {
   if (!this.hasSecondsValue) {
      this.secondsValue = 0;
    }
    this.interval = setInterval(() => {
      this.secondsValue++;
    }, 1000);
  }

  disconnect() {
    clearInterval(this.interval);
  }

  secondsValueChanged() {
    this.element.textContent = `Timer: ${this.secondsValue} seconds`;
  }
}
```
```html
<div data-controller="timer"
     data-timer-seconds-value="0">
</div>
```
</div>
