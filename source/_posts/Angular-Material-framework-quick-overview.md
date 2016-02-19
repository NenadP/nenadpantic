---
title: Angular Material framework quick overview
date: 2016-02-18 23:45:53
tags: ["JavaScript", "AngularJS"]
---

[Angular Material][1], at the time of writing, is at 1.0.5, and in pretty stable shape. It's official angular implementation of the [Google Material design][2]. Google own framework - abstract of JavaScript implementation, is **Polymer** - I did a bit of a digging and here's how they implement**** [components][3]. There are some other implementations - like [Materialize][4] - also standalone framework, or [MaterialUI][5] - tailored for React framework.

Good thing about **Google Material** in general is the huge [Book of Standards][2] that the Google design team wrote, specifying in detail how these components are to be used, and why it's good for UX that way. That could help a lot, embracing, what I suspect is, enormous work done by Google team.

Google Material is taking over the Google products one by one, so it is likely that most of the internet users are used to its **look and feel**. That's double edged sword - you might, or might not want to look like Google.

It's look and feel is **flat, tidy, colorful**, with large sized components; buttons and other interactive elements have distinct **"Ink" ripple effects** - it is mobile first, yet gone desktop too. There are lots of "touchy" **animations**. In a certain way, it's a bit "playful", bright, optimistic. On the very edge to be too playful for certain kind of businesses.

Talking about Angular Materials itself, they have implemented most of the components defined in Google Material "Bible". Be warned though: **there is no table implementation**, and it has been constantly postponed, and at the time of writing, it's sitting in the Backlog. If you need tables, you will be forced to roll your own, or use something like [this][6] or [that][7], which are not fully stable, yet usable  implementations - risking, of course, that Angular Material team can roll proper implementation at some point.

You will need to install separately **Roboto Webfont and Material Icons** - they are not shipped wit the library. This can be somewhat painful. Also, if you need to use non-canonical icons, you might want to look at the [mdi][8] - extended library of Material icons - including **community created** ones.

I was hoping I will be given set of classes and hoping to write as less CSS possible. Don't get me wrong, I love CSS, but I prefer to have set of predefined tools for adjusting the details. That's not the case - you will need to introduce your own CSS tweaks if you want extra customisation. But here goes the magic - use of [**Flexbox**][9] instead of Grid system!

It's the cutting edge technology, and you will need to **forget about "older" IE support** without painful fallbacks. It is a pain and joy to play with a flexbox, and it is in heart and soul of Angular Material.

Also, they rolled out really good support for responsive layout by implementing **variety of responsive breakpoints**.

You can easily define your overall colour scheme look and feel by setting it up at the Angular app config time:

```javascript

angular.module('myApp', ['ngMaterial']).config(function ($mdThemingProvider) {
  $mdThemingProvider.theme('default')
    .primaryPalette('pink')
    .accentPalette('orange')
    .warnPalette('deep-orange')
    .backgroundPalette('lime')
});
```
... and your components will automagically start to get the colours as per specs.
Of course, you will need to write some CSS if you want to introduce some "heresy" in the Google devised UI rules. But, you could **define your own set of colours** and hues too - in fact, I found a nice resource on the net - [Palette Generator][11] - you might find it very useful.

**Directives are very well done**, I did not encountered major issues working with them. They are made with flexibility in mind, they are "**transcludable**" so it's easy to mix your angular workings with them. Also, for complex components there are services which add a layer of extra control on components. They are very useful, configuration code is easy to use. Overall, I got impression of **high JS code quality**.

Documentation provided is for the most of the time good, with ability to jump between source and examples, and they use [CodePen][10] to provide them.

[Team at the Github][12] is working diligently, lot's of development going on; they **answer to the issues** quickly and efficiently.

I recommend giving it a test drive - it is well worth looking into it if you want Materials in your Angular app. [Check it out][1].



[1]: https://material.angularjs.org/latest/
[2]: https://www.google.com/design/spec/material-design/introduction.html#
[3]: https://elements.polymer-project.org/browse
[4]: http://materializecss.com/
[5]: http://www.material-ui.com/
[6]: http://iamisti.github.io/mdDataTable/
[7]: http://danielnagy.me/md-data-table/
[8]: https://materialdesignicons.com/
[9]: https://css-tricks.com/snippets/css/a-guide-to-flexbox/
[10]: http://codepen.io/team/AngularMaterial/
[11]: http://mcg.mbitson.com/#/
[12]: https://github.com/angular/material

