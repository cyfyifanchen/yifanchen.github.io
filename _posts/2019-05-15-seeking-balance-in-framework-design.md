---
title: "Seeking the Balance in Framework Design"
layout: post
date: 2019-5-15
tag:
- dev
blog: true
star: false
---
<iframe width="1917" height="716" src="https://www.youtube.com/embed/ANtSWq-zI0s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> Frameworks should be distinguished by the design tradeoffs they offer on scope, render mechanism, and state mechanism, rather than on popularity and community based metrics.

## Scope

Scope refers to what the framework tries to do for its users. Developers need understand the pros and cons to each approach.

### Large-scoped frameworks

Large-scoped frameworks such as Angular or Aurelia favor a top down design, in which most of the conceivable issues that developers will run into have already been factored into the framework design. Features like validation, animation, internationalization, or accessibility are baked into the framework, so developers do not have to implement and integrate their own solutions.

Frameworks which encompass a large scope may be productive in the short-term with their optimized, built-in abstractions covering most common problems. The associated ecosystem of user-defined libraries may as a result be more consistent and coherent. On the downside, that ecosystem may be smaller. The built-in abstractions may require additional learning and training.

Highly focused frameworks have fewer concepts to get started with. The larger flexibility allows for a large ecosystem from which user can build arbitrarily complex systems. For the framework team, the smaller maintenance surface means they can more easily explore new ideas (React introducing Hooks) and optimizing their area of focus (React Concurrent Mode). However, users may need to spend time picking up and integrating a sometimes large set of extra libraries with largely varying levels of maintenance and documentation.

The Progressive approach takes pros and cons from both sides. Developers for instance often celebrate how easy it is to get started with Vue, and the documentation of officially supported libraries. However, Progressive frameworks share the same maintenance burden as frameworks with a large scope, while not being able to exhibit an ecosystem as rich as highly focused frameworks.

### Small-scoped frameworks

On the other end of the scope dimension are highly focused frameworks. Such frameworks are organically built bottom-up by the community around a highly focused core. React for instance sees itself as focusing on the view layer of front-end applications, with other specialized libraries coming together to handle additional concerns such as data fetching (relay), or side-effects (redux-saga).

### Vue falls in middle

Placing the Vue.js framework somewhat in the middle (Progressive framework). On the one hand, Vue largely focuses on the view layer. On the other hand, Vue’s layered design allows for opt-in, official, documented solutions for common problems.


## Rendering Mechanism

The second dimension of analysis is the view rendering mechanism. This involves how the UI structure is expressed, and how the UI is rendered.

On the one hand, in frameworks using `JSX`, or its `TypeScript` version `TSX` (such as React, or Stencil), developers can use the full power of the Turing-complete underlying language to express arbitrarily complex logic. Those frameworks usually see the view as data (virtual DOM), with large customization opportunities in user land, including using view data for rendering to alternative targets (rendering into a terminal, or to pdf). On the negative side, the fully dynamic nature of render functions makes it hard to optimize for by default. Such frameworks, like React, may include escape hatches to enable developers to optimize rendering themselves (React’s shouldComponentUpdate and useMemo). Optimizing rendering in those frameworks involves a significant learning phase, as developers may have to deeply acquaint themselves with implementation details of the framework.

On the other hand, template-based frameworks such as Vue or Svelte, bound the expressiveness of the rendering function to the capability of the template language. Templates are harder to customize out of the possibilities already considered in the template language. The rigid structure however enables optimized-by-default rendering of the UI. In Svelte, for instance, the following template

```
<h1> Hello {name} </h1>
```

will result in running the following compiled code when name changes, updating chirurgically only the part of the DOM which needs to be changed:

```
p(changed, ctx){
  if (changed.name) {
    set_data (t1, ctx.name)
  }
}
```

Such by-default optimizations are difficult to achieve for frameworks which use a virtual DOM and compute the DOM operations to perform in case of updates by keeping track and diffing two versions of a virtual DOM – thus exhibiting a higher memory and CPU usage profile.

Evan notes that Vue strikes a middle ground by being template-based by default, with by-default rendering optimizations, while still letting developers falling back to full-fledged JavaScript render functions when the need arises.

As a third dimension to evaluate framework on, Evan mentions the mechanism by which state is managed by the framework, in particular the reactivity and data synchronization abilities offered by the framework.

Evan, in his presentation, doubts the existence of a universally best framework:

> The framework landscape is like a multi-dimensional space with multiple ever-moving entities, each seeking its own balance point. Where is the perfect balance point? Is a single perfect balance point even optimal for JS devs as a whole? There isn’t a single Good vs. Bad spectrum for frameworks.

Developers need to understand front-end framework design tradeoffs and how that fits the requirements of their projects.

## State Mechanism

*Evan didn't give much insights regarding the differences of State Mechanism due to the duration of the talk, I am going to do some research and complete it later on*