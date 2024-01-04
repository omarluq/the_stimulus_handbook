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

<div class='flex flex-col items-center justify-center'>
  <h1> Presented By </h1>
  <img src="/IMG_1997.jpg" class="h-40 rounded-full" />
  <h2 class='text-2xl font-bold mt-3'>Omar Luq</h2>
  <p class='text-lg'>Software Engineer</p>

  <div class='flex flex-row gap-4 mt-4'>
    <a href="https://github.com/omarluq" target="_blank" class="no-underline">
      <Item text="mygithub">
        <CarbonLogoGithub />
      </Item>
    </a>
    <a href="linkedinhttps://www.linkedin.com/feed/" target="_blank" class="no-underline">
      <Item text="sli.dev">
        <CarbonLogoLinkedin />
      </Item>
    </a>
  </div>
</div>

---
transition: slide-left
---
<h1> What is StimulusJS </h1>
<p> Stimulus is a lightweight and minimalistic JavaScript framework. Instead of focusing on HTML rendering, it boosts HTML elements by leveraging data attributes. </p>

<div class='pb-2'><span style="color: #007bff;">💡</span> <strong>Flexibility:</strong> Unlike many other frameworks that come with a heavy set of rules and structures, Stimulus takes a more flexible approach.</div>
<div class='pb-2'><span style="color: #28a745;">🌐</span> <strong>HTML Enhancement:</strong> Its basic concept is to enhance existing HTML. Instead of requiring developers to rewrite or replace their HTML, Stimulus augments it, tapping into the power of data attributes.</div>
<div class='pb-2'><span style="color: #dc3545;">🔗</span> <strong>Harmonious Integration:</strong> This design promotes a harmonious blend of JavaScript's dynamic capabilities with the foundational structure of web content.</div>
<div>
<div class='flex flex-row gap-5 pt-1'>
```js
import { Controller } from "@hotwired/stimulus"

export default class GreeterController extends Controller {
  // ...
}
```
```html
<div data-controller="greeter"></div>
```
</div>
</div>

---
transition: slide-left
---
<h1> Getting started with StimulusJS </h1>
<div class='pb-2'>
<span style="color: #007bff;">🔧</span> <strong>Installation:</strong>
</div>
<div class='pb-2'>
1. Install with NPM or any other tool supported
</div>
<div class='pb-2'>
```bash
npm install @hotwired/stimulus
```
</div>
<div class='pb-2'>
2. After installing, import and initialize Stimulus in the main JavaScript file:
</div>
<div class='pb-2'>
```js
import { Application } from '@hotwired/stimulus'

window.Stimulus = Application.start()

```
</div>
<div class='pb-2'>
3. Create Controller and Register it
</div>
<div class='pb-2 flex flex-row gap-3'>
```js
import { Controller } from "@hotwired/stimulus"

export default class HelloController extends Controller {
  connect() {
    console.log("Hello from Stimulus!");
  }
}
```

```js
import { Application } from "@hotwired/stimulus"
import HelloController from "./controllers/hello_controller"

window.Stimulus = Application.start()

Stimulus.register("hello", HelloController)
```
</div>

---
transition: slide-left
---
<h1>Controllers in StimulusJS</h1>
<p>Controllers are basic organizational units that provide the primary means of adding behavior to HTML elements.</p>
<div class='list-none text-sm'>
  <li class='pb-2'>
    <span style="font-weight: bold; color: #007bff;">&#9679; Connection to HTML:</span> Controllers are JavaScript classes that connect to HTML elements via data attributes, providing a clear and structured connection between HTML and JavaScript.
  </li>
  <li class='pb-2'>      
    <span style="font-weight: bold; color: #28a745;">&#9679; Lifecycle:</span> Each controller has lifecycle callbacks, <code>connect()</code> and <code>disconnect()</code>, allowing the set up and tear down of JavaScript code in an organized way.
  </li>
  <li class='pb-2'>      
    <span style="font-weight: bold; color: #dc3545;">&#9679; Reusability:</span> Controllers can be reused across an application, leading to more maintainable and module code.
  </li>
</div>
<div class='flex flex-row gap-5 pt-1'>
```js
import { Controller } from "@hotwired/stimulus"

export default class GreeterController extends Controller {
  connect() {
    this.element.innerText = "Hello World!"
  }

  disconnect() {
    console.log("Goodbye World!");
  }
}
```
```html
<div data-controller="greeter"></div>
```
</div>

---
transition: slide-left
---
<h1>StimulusJS APIs</h1>
<p> 
In the realm of StimulusJS, there are a set of advanced features and patterns that significantly elevate the developer experience. These features, akin to APIs, offer pre-defined behaviors or functionalities that can seamlessly integrate into HTML elements. This streamlines the creation of interactive and dynamic web interfaces.
By encapsulating common tasks and behaviors, these APIs make code not only more concise but also easier to read and maintain. As of Stimulus 3.2, the Controller class includes these notable APIs:
</p>  
<div class='pb-1'><strong>🎨 Classes API:</strong> Streamlines CSS classes manipulation on controller elements.</div>
<div class='pb-1'><strong>🎯 Targets API:</strong> Facilitates DOM elements referencing and management as targets within a controller.</div>
<div class='pb-1'><strong>🔢 Values API:</strong> Simplifies data management and transfer between HTML and JavaScript.</div>
<div class='pb-1'><strong>⚡ Actions API:</strong> Enables the binding of JavaScript functions to DOM events directly in HTML markup.</div>
<div class='pb-1'><strong>🔌 Outlets API:</strong> Allows for cross-controller communication and coordination.</div>
---
transition: slide-left
---
<h1>Classes API</h1>
<p><code>Classes API</code> allows to define a structured list of CSS class names within a controller. This helps in maintaining a clear connection between JavaScript and CSS. While it doesn't automatically manage class states based on property changes, it provides a declarative way to handle class names, improving code readability and organization.</p>

<div class='flex flex-row gap-5'>
```js
import { Controller } from "@hotwired/stimulus"

export default class ToggleController extends Controller {
  static classes = ["active"]

  connect() {
    if (this.hasActiveClass) {
      this.interval = setInterval(() => {
        this.element.classList.toggle(this.activeClass)
      }, 10000); // Toggles class every 10 seconds
    }
  }

  disconnect() {
    clearInterval(this.interval);
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

---
transition: slide-left
---
<h1>Targets API</h1>
<p>The <code>Targets API</code>, enhances controllers by allowing direct references to specific DOM elements. By defining targets, we avoid complex query selectors and ensure a clean separation between JavaScript and HTML structure. Moreover, Stimulus provides lifecycle callbacks for each target, which gives precise control over their behavior as they are added to or removed from the DOM.</p>
<div class='flex flex-row gap-5 max-h-fit'>
```js
import { Controller } from "@hotwired/stimulus"

export default class ToggleController extends Controller {
  static classes = ["active"]
  static targets = ["toggleElement"]

  toggleElementTargetConnected(element) {
    if (this.hasActiveClass && this.hasToggleElement) {
      this.interval = setInterval(() => {
        element.classList.toggle(this.activeClass)
      }, 10000); // Toggles class every 10 seconds
    }
  }

  toggleElementTargetDisconnected(_element) {
    clearInterval(this.interval);
  }
}
```
```html
<div data-controller="toggle">
  <div data-toggle-target="toggle-element"
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

---
transition: slide-left
---
<h1>Values API</h1>
<div>The <code>Values API</code> in Stimulus powers up controllers with data management. This feature links HTML data attributes to JavaScript properties.</div>

<div class='py-2'><strong>Types</strong>: <div class='text-sm'>Define the type of data values should hold. Supported types: <code>String</code>, <code>Number</code>, <code>Boolean</code>, <code>Array</code>, <code>Object</code></div>
</div>

<div class='py-2'><strong>Value Properties:</strong>
  <div class='list-none text-sm'>
    <div>🔹 <code>[name]Value</code> Getter for the value.</div>
    <div>🔹 <code>[name]Value=</code> Setter for the value.</div>
    <div>🔹 <code>has[name]Value</code> Existential property for a value evaluates to true when the associated data attribute is present on the controller’s element and false when it is absent.</div>
  </div>
</div>

<div class='py-2'>
  <strong>Change Callbacks</strong>:
  <div class='text-sm'>Define a method <code>[name]ValueChanged</code> in the controller, where [name] is the name of the value to be observed for changes.</div>
</div>

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

---
transition: slide-left
---
<h1>Actions API</h1>
<p>The <code>Actions API</code> in Stimulus handles connecting DOM events to a controller. An action is a connection between a controller method, a controller element and a DOM event listener</p>
<div class='pb-2'><span style="color: #28a745;">🎯</span> <strong>Declarative Syntax:</strong> It uses a declarative syntax that makes the HTML templates more readable and easier to understand.</div>
<div class='pb-2'><span style="color: #dc3545;">🖱️</span> <strong>Interactive Elements:</strong> Ideal for adding interactivity to elements like buttons, links, and forms.</div>
<div class='flex flex-row gap-5 pt-1'>
```js
import { Controller } from 'stimulus';
export default class GreeterController extends Controller {
  greet(event) {
    event.stopPropagation()
    alert('Hello!');
  }
}
```
```html
<div data-controller='greeter'>
  <button data-action="click->greeter#greet">
    Say Hello
  </button>
</div>
```
</div>


---
transition: slide-up
---
<h1>Outlets API</h1>
<p>The <code>Outlets API</code> allows referencing controller instances and their associated elements from within another Controller by using CSS selectors. It is conceptually similar to the <code>Targets API</code> but with the difference that they reference a controller instance. Outlets are meant to help with cross-controller communication and coordination</p>

<div class='pb-2'><span style="color: #007bff;">🔌</span> <strong>Defining Outlets:</strong> <span class='text-sm'>Declare outlets in a controller using the <code>static outlets</code> array. This declares which other controller identifiers can be used as outlets on this controller.</span></div>
<div class='pb-2'><span style="color: #28a745;">🎯</span> <strong>HTML Setup:</strong> <span class='text-sm'>Use <code>data-[identifier]-[outlet]-outlet</code> attributes in the HTML and its value is as a CSS selector which can be used to refer to other controller elements defined as outlets on the host controller.  The outlet identifier in the host controller must be the same as the target controller’s identifier.</span>
</div>
<div class='pb-2'><span style="color: #dc3545;">🔗</span> <strong>Properties:</strong><span class='text-sm'> For each outlet defined in the static outlets array, Stimulus adds five properties to the controller, where [name] corresponds to the outlet’s controller identifier:</span>
<div class='list-none list-inside text-sm'>
  <li><code>has[Name]Outlet</code> Checks if a [name] outlet is present in the controller and return a Boolean.</li>
  <li><code>[name]Outlet</code> Returns the Controller instance of the first [name] outlet. Throws an exception if not present.</li>
  <li><code>[name]Outlets</code> Returns an Array of all Controller instances of the [name] outlets.</li>
  <li><code>[name]OutletElement</code> Returns the DOM element of the first [name] outlet. Throws an exception if not present.</li>
  <li><code>[name]OutletElements</code> Returns an Array of DOM elements of all [name] outlets.</li>
</div>
</div>


---
transition: slide-left
---
<div class='pb-2'>
  <span style="color: #007bff;">☎️</span> <strong>Outlet callbacks:</strong>
  <p class='text-sm'> Outlet callbacks are specially named functions called by Stimulus to handle responding to whenever an outlet is added or removed from the page. To observe outlet changes, define a function named <code>[name]OutletConnected()</code> or <code>[name]OutletDisconnected()</code> </p>
</div>


---
transition: slide-left
---
<h1>Outlets API Example</h1>
<div class='flex flex-row gap-5'>
```html
<div id='users-list'>
  <div id='user-1'
       class="online-user"
       data-controller="user-status">
    <div data-user-status-target='image'></div>
    <div data-user-status-target='name'></div>
    <div data-user-status-active-value='false'></div>
  </div>
  <div id='user-2'
       class="online-user"
       data-controller="user-status">
    <div data-user-status-target='image'></div>
    <div data-user-status-target='name'></div>
    <div data-user-status-active-value='false'></div>
  </div>
</div>

<div id='chat-box-1'
     data-controller="chat-box"
     data-chat-user-status-outlet=".online-user">
  <div id='online-users-images-row' 
       data-chat-target='online-users'></div>
</div>
```

```js
export default class ChatBoxController extends Controller {
  static outlets = [ "user-status" ]
  static targets = [ "online-users" ]

  connect() {
    this.userStatusOutlets.forEach( statusOutlet => {
      if (statusOutlet.activeValue) {
        this.onlineUsersTarget.appendChild(
          statusOutlet.imageTarget
        )
      }
    })
  }

  userStatusOutletConnected(outlet, element) {
    this.onlineUsersTarget.appendChild(outlet.imageTarget)
  }

  userStatusOutletDisconnected(outlet, element) {
    this.onlineUsersTarget.removeChild(outlet.imageTarget)
  }
}
```
</div>

---
transition: slide-left
---
<div class='flex flex-col items-center justify-center'>
  <h1> The End</h1>
  <img src="/IMG_1997.jpg" class="h-40 rounded-full" />
  <h2 class='text-2xl font-bold mt-3'>Omar Luq</h2>
  <p class='text-lg'>Software Engineer</p>

  <div class='flex flex-row gap-4 mt-4'>
    <a href="https://github.com/omarluq" target="_blank" class="no-underline">
      <Item text="mygithub">
        <CarbonLogoGithub />
      </Item>
    </a>
    <a href="linkedinhttps://www.linkedin.com/feed/" target="_blank" class="no-underline">
      <Item text="sli.dev">
        <CarbonLogoLinkedin />
      </Item>
    </a>
  </div>
</div>
