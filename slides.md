name: dblue
layout: true

class: bg-dark, center, middle

---

name: lblue
layout: true

class: bg-light, center, middle

---

class: title

# Tools, Tips & Tricks for building Componentised Web Apps

* <span class="speaker">Phil @leggetter</span>
* <span class="speaker-job-title">Head of Evangelism</span>
* <span class="speaker-pusher-logo"></span>

???

---

template: dblue
class: bg-contain, pusher-circle
background-image: url(./img/pusher-circles.png)

---

background-image: url(./img/caplin-trader-examples.png)
class: trans-h

# Caplin Systems

???

---

background-image: url(./img/caplin-trader.png)

???

---

template: dblue
class: bg-contain
background-image: url(./img/brjs-site.png)

???

---

template: dblue
class: bg-contain
background-image: url(./img/brjs-video-compilation.png)

???

* ~10 events
* Guessing how James found me
* STV TechTalks
* DunDDD
* QCon London
* Fluent
* FOSDEM
* FutureJS
* Devoxx
* FED London
* DevWeek

---

# Fundamentally about Building Componentised Web Apps

---

## What I'll Cover

* Questions & Ideas
* 5 Tools, Tips & Tricks

---

## What I'll Cover

* Questions & Ideas
* ~~5 Tools, Tips & Tricks~~
--

* 5 Lessons Learned
--

* Answers from Lessons Learned

---

# But, What are Components?

---

class: top

## What are Components?

--

* DOM Elements?
--

* ~~Widgets~~
--

* Application Modules?
--

* Application Features?
--

* Application Services?

---

class: bg-video, em-text, trans-h, top, vid-width-100

<video id="video" autoplay="true" loop="true">
	<source src="./img/pusher-debug-console.mp4" type="video/mp4">
</video>

???

* left-hand menu
* Central Console
  * Rows
	* Expandable rows
* Right-hand Event Creator

---

# Can all components be Web Components?

---

[Christian Heilmann: Web Components and You - Dangers to Avoid](http://christianheilmann.com/2014/04/18/web-components-and-you-dangers-to-avoid/)

> Just because we can make everything into an element now, doesn’t mean we should

--

## Why not?

---

# Component Best Practice?

---

background-image: url(./img/first.gif)
class: bg-contain, first-slide, trans-h, top

[addyosmani.com/first/](http://addyosmani.com/first/)

---

> Components Should Be Focused, Independent, Reusable, Small & Testable 

[Addy Osmani](https://twitter.com/addyosmani)

---

class: first-slide

## Component Best Practice

* **F**ocused - How focused?
--

* **I**ndependent - kinda
--

* **R**eusable - Maybe
--

* **S**mall - It depends!
--

* **T**estable &#10004;


???

* Independent - live in isolation without external dependencies.

---

## Questions

* What are components in your App architecture?
* Can all components be Web Components?
* What are the best practices for building components?

---

# 5 Lessons Learned

---

# 1. Three Application Component Types

---

## Reusable Elements

---

> Some developers find it more feasible to build an integrated solution first and then extract out useful modules. This can save time on public interfaces that might turn out to be wrong

[addyosmani.com/first/](http://addyosmani.com/first/)

---

> Some developers find it more feasible to build an integrated solution first and then extract out useful modules. **This can save time on public interfaces that might turn out to be wrong**

[addyosmani.com/first/](http://addyosmani.com/first/)

---

## Application Features

**TODO: What are application features?**

---

## Application Services

**What are application services?**

---

# 2. Develop Features in Isolation

---

**TODO: explain what this means using Pusher Debug Console example**

* assets, faster load etc.

---

## Use Tooling

---

# 3. Avoid Premature Feature Abstraction

---

# 4. Do Abstract Services

---

# 5. Do Abstract the UI layer

---

# Bonus

## End to End Testability?

???

Addy's initial version was FIRS and not FIRST

---

**TODO: explain End to End Testability**

---

# Questions Answered

---

## What are components in your App architecture?
--

* Reusable Components
* Application Features
* Application Services
--

* The Application itself?

---

class: bg-contain, top
background-image: url(./img/angular-2-my-app.png)

# Angular 2

---

## Can all components be Web Components?
--

* Provides a structure for building componentised web apps
* Reusable Elements & Features - yes
* Work within "best practice" constraints
* Services - ?
* The App - ?

---

## What are the best practices for building components?
--

* **F**ocused - reusable element, feature or service
* **I**ndependent - dev in isolation. Loose coupling of UI & Services
* **R**eusable - but only with care
* **S**ervices - essential
* **T**estable - because it's Isolated

---

class: bg-dark

# Componentised Web Apps Now

---

**TODO: lab.poll.io for currently used UI solutions**

---

class: top

## Componentised Web Apps Now - questions.

*Should native browser support stop us thinking about building
componentised web apps?*

--

**No!**

--

*Should we be build componentised web apps anyway?*

--

**We're already building web apps out of components *right now*!**

---

class: inverse, center, middle, section-start

# JavaScript
# Libraries & Frameworks

???

* Because they all have a concept called "Components"

---

class: code-reveal, top, long

### AngularJS

--

```xml
<script src="js/angular.min.js"></script>
```

--

```xml
<script>
angular.module('demo', [])
	.directive('ngAvatar', function () {
		return {
```

--

```js
			restrict:"AEC",
```

--

```js
			scope: {
				service: '@',
				username: '@'
			},
```

--

```xml
			template: '<img src="http://avatars.io/' +
					  '{{service}}/{{username}}" />'
		};
	});
</script>
```

```xml
<body ng-app="demo">
```

--

```xml
	<ng-avatar service="twitter" username="leggetter" />
```

--

<div ng-app="demo" style="text-align: center; margin-top: 20px;">
	<ng-avatar service="twitter" username="leggetter" />
</div>

???

* A - attribute on element, E - element, C - class name

---

class: code-reveal, top, long

### EmberJS

--

```xml
<script src="js/jquery-1.10.0.min.js"></script>
```

--

```xml
<script src="js/handlebars.js"></script>
```

--

```xml
<script src="js/ember.js"></script>
```

--

```xml
<script>
	var App = Ember.Application.create();

	App.EmAvatarComponent = Ember.Component.extend({
```

--

```js
		url: function () {
			return 'http://avatars.io/' +
					this.get( 'service' ) + '/' +
					this.get( 'username' );
		}.property( 'username' , 'service' )
	});
</script>
```

--

```xml
<script type="text/x-handlebars" id="components/em-avatar">
	<img {{bind-attr src=url}} />
</script>
```

--

```
<script type="text/x-handlebars">
	{{em-avatar service="twitter" username="leggetter"}}
</script>
```

http://jsbin.com/fexawujibe/2/edit?html,output

???

* Sorry - no demo. You get the idea.
* http://jsbin.com/fexawujibe/2/edit?html,output


---

class: code-reveal, top, long, wide

### ReactJS

--

```xml
<script src="js/react.js"></script>
<script src="js/JSXTransformer.js"></script>
```

--

```xml
<script type="text/jsx">
var ReAvatar = React.createClass({
	render: function() {
		return (
			<img src={"http://avatars.io/" +
					this.props.service + "/" +
					this.props.username} />
		);
	}
});
```

--

```js
React.renderComponent(
	<ReAvatar service="twitter" username="leggetter" />,
	document.querySelector('re-avatar')
);
</script>
```

--

```xml
<re-avatar />
```

--

<div style="text-align: center; margin-top: 20px;">
	<re-avatar />
</div>

---

### Many More...

* [KnockoutJS Components](http://knockoutjs.com/documentation/component-overview.html)
* [Backbone components](https://github.com/malroc/backbone-component)
* [Backbone with React components](https://github.com/magalhas/backbone-react-component)
* [CanJS components](http://canjs.com/guides/Components.html)

And...

???

* KO introduced components in 3.2


---

background-image: url(img/layers-of-polymer.png)
class: trans-h, center

???

* Material design
* Paper elements

---

class: code-reveal, top, wide

## Polymer

```xml
<script src="webcomponentsjs/webcomponents.min.js"></script>
<link rel="import" href="polymer/polymer.html">
```

--

```xml
<polymer-element name="po-avatar" attributes="service username">
```

--

```xml
	<template>
		<img src="http://avatars.io/{{service}}/{{username}}" />
	</template>
```

--

```xml
	<script>
		Polymer('po-avatar', {});
	</script>
</polymer-element>
```

--

```xml
<po-avatar service="facebook" username="leggetter" />
```

--

<div style="text-align: center; margin-top: 30px;">
	<po-avatar service="facebook" username="leggetter" />
</div>

---

background-image: url(img/polymer-paper-elements.png)
class: bg-cover

---

background-image: url(img/md-angularjs.png)
class: bg-cover

---

class: top, long, wide

## Who's Building Componentised Web Apps now?

--

Angular, Ember, Backbone, Knockout, React, Web Components with Polyfills, Polymer

## **You** probably are already

```xml
<ng-avatar service="twitter" username="leggetter" />
```

vs.

```xml
<my-avatar service="twitter" username="leggetter" />
```

---

class: trans-all
background-image: url(img/poly-mail.png)

## Examples

* [From Eric's Slides](http://polymer-change.appspot.com/#19)
	* [GitHub](https://github.com/)
	* Chrome OS
* [GMail built in Polymer](https://poly-mail.appspot.com/)
* [Topeka game built in Polymer](https://www.polymer-project.org/apps/topeka/)

???

* GitHub time inspect element

---

class: bg-dark

# Why Web Components are the future!

---

# 1. You're already building componentised web apps

## If you're not, you probably should be

---

# 2. Trends & Demand

---

## Libraries

* Alignment toward Web Components
* Angular - Directives
* Ember - Components
* Knockout - Components
* Polymer - build upon Web Components
* Angular 2...

---

class: bg-cover
background-image: url(img/angular-2-component.png)

---

## Browser Vendor Support

* Google
* Opera - uses Blink
* Mozilla
* Microsoft - ?
  * previously: HTA & ASP.NET Controls
	* In high demand on IE UserVoice
* Apple - ?

???

* Libraries: Angular, Ember, KO all very much align
* Whether we like Google or not, they are pushing the web forward
* Mozilla seem to be on board with web components
* MS actually did this previously with HTA and behaviours

---

template: lblue
class: bg-video, em-text, trans-h

<video id="video" autoplay="false" loop="false" controls="true">
	<source src="/img/ie-uservoice.mp4" type="video/mp4">
</video>

## In Demand

???

* Positions 2, 3, 5 & 6

---

class: middle, center

# 3. Encourages good software development

## [Component-based Development](http://en.wikipedia.org/wiki/Component-based_software_engineering)

---

class: long, wide

## Separation of Concerns

```xml
<!doctype html>
<html>
	<head>
		<meta charset="utf-8">
		<title>A new Gmail?</title>
		<meta name="description" content="">
	</head>
	<body>

		<header>
			<img src="img/logo.png" alt="Google Logo" />
			<gmail-search />
			<gmail-account-strip />
		</header>

		<gmail-side-bar>
			<nav is="gmail-labels"></nav>
			<gmail-contacts />
		</gmail-sidebar>
		<main>
			<nav is="gmail-categories"></nav>
			<gmail-email-list />
		</main>

		<gmail-talk />
	</body>
</html>
```

???

* HTML / Content, CSS / Presentation / JS Behaviour
* We start to build our apps out of components
* Each component does a specific thing
* Each has its own functional concern

---

## Encapsulation

* Shadow DOM - Style & DOM encapsulation
* Does *NOT* offer JavaScript protection

####  Hacky Custom Element

<link rel="import" href="./assets/hack-test.html" />

<hack-test></hack-test>

???

---

## Loose Coupling

* Custom Events
* Element API (interface)
* Existing messaging frameworks

???

* through component APIs

---

class: wide, long, top, code-reveal

## Custom Events

```xml
<script>
	var CustomEventPrototype = Object.create(HTMLElement.prototype);
	CustomEventPrototype.createdCallback = function() {
	  // Build element ...
	  
	  this.addEventListener('click', function() {
	    var customEvent = new CustomEvent('cheese');
	    this.dispatchEvent(customEvent);
	  }.bind(this));
	};

	// ...
```

--

```xml
	var customEl = document.getElementById('my_custom_ev');
	customEl.addEventListener('cheese', function() {
	  alert('cheese fired!');
	});
</script>

<custom-event-ex id="my_custom_ev"></custom-event-ex>
```

<custom-event-ex id="my_custom_ev"></custom-event-ex>

---

class: wide, long, top, code-reveal

## Element API Attributes & Methods

```xml
<script>
	CustomEventPrototype.startSpin = function() {
	  this.img.classList.toggle('spin');
	};
	
	CustomEventPrototype.stopSpin = function() {
		this.img.classList.toggle('spin');
	};
	
	// ...
	
	var spinEl = document.getElementById('spin_el');
	spinEl.startSpin();
	
	// ...
	
	spinEl.stopSpin();
</script>

<custom-event-ex id="spin_el"></custom-event-ex>
```

<custom-event-ex id="spin_el"></custom-event-ex>

---

## Supports Change

???

* loose coupling E.G. interaction through APIs
* Important on the Web where changes happen so fast

---

class: wide

## Reusability

```xml
<link rel="import" href="https://some-cdn.com/my-avatar.html" />
```

???

---

## High Cohesion

```
myavatar.html
├── js/script.js
├── css/styles.css
└── img/bg.png
```

???

* Functional cohesion - everything that's related together (HTML imports)

---

class: middle, center

## Problems? Solved in the future?

* HTML Imports
  * Vulcanize | HTTP2
* Shared scripts?
	* Cache
* Multiple versions?
* Better Cross-component communication?
* Allow `<link>` for CSS in Shadow DOM?

???

* HTTP2: Loading page elements in parallel over a single TCP connection

---

class: top, fixed-ul, wide, long, bg-dark

## Summary


* Custom Elements - **Awesome**

--

* HTML Templates, Shadow DOM, HTML Imports - **Native FTW**

--

* You *can* & *are* building componentised web apps now

--

* Trends & "best practice" &hearts; Web Components

--

* **Web Components are the future!**

???

* Custom Elements - foundation of Web Components. The building blocks of apps to come.
* Custom Elements - declarative, readable, support extension, native benefits

---

## Resources

* http://pusher.com - easily add realtime messaging to your apps
* http://webcomponents.org/
* https://www.polymer-project.org
* [Eric Bidelman's Google IO 2014 talk](http://polymer-change.appspot.com/)
* [Angular Material](https://material.angularjs.org/)
* [Google Material Design](http://www.google.com/design/spec/material-design/introduction.html)
* [HTML Template Chooser](http://garann.github.io/template-chooser/)
* [IE UserVoice forum](https://wpdev.uservoice.com/forums/257854-internet-explorer-platform/filters/top)
* [Source for these slides](https://github.com/leggetter/web-components-now/tree/devweek-2015)

---

class: title

# Why you should be using Web Components Now. And How.

## Questions?

[leggetter.github.io/web-components-now](leggetter.github.io/web-components-now)

* <span class="speaker">Phil @leggetter</span>
* <span class="speaker-job-title">Head of Evangelism</span>
* <span class="speaker-pusher-logo"></span>
