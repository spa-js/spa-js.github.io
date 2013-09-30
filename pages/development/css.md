---
layout: default
title: Development - CSS
category: bp
---



# CSS Development


## Responsive Web Design

Responsive web design has been a hot topic of late. Effectively, it means that the app responds sensibly to sizing and rotation events.

For desktops, it does look cool to have everything re-flow dynamically when you change the browser's width, but I've always considered that as eye-candy more than proper functionality. It has its place, but most users are not whipping the browser size around all that often. Don't go overboard with dynamic resizing. Adapt your primary page on app startup and make "functional only" changes should the user change the browser size. The rest is just "wow" factor for demos.

For mobile devices, there is a different use case. Since mobile web and hybrid apps are always full screen, there are effectively two possible form factors or sizes; phone (small) and tablet (large), and two orientations; portrait and landscape. Your app should reasonably support both form factors. For tablets, you either provide more details on each view, or maintain a constant navigation section. Orientation changes can be handled either by simply resizing the page and allowing scrolling to happen naturally, or by re-organization of the layout (such as moving navigation from the top to the left). Both are reasonable solutions, but are dependent on the apps overall visual design requirements.

- [HTML5 And CSS3 Responsive Web Design Cookbook](http://www.creativealys.com/2013/09/27/html5-and-css3-responsive-web-design-cookbook/) - A comprehensive free ebook that details various responsive techniques


## Proper layouts using Flexbox

Flexbox is a revolution in clean CSS based layout. Yes, I'm talking to all of you that are still using `<table>` tags or layout, which while a simple cheat, has been a major no-no for years. The only alternatives for layout were either a nightmare of floating and positioned divs, or some 3rd party CSS library like [Bootstrap](http://getbootstrap.com/). There is finally a standards based and easy to use (honest!) solution. It is supported by all major browers, with the downside of IE where support starts with version 10.

- [A complete guide to Flexbox](http://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [A showcase of traditionally hard CSS problems, easily solved using flexbox](http://philipwalton.github.com/solved-by-flexbox)





## Style Guides

Your company should adopt a standard style guide for coding in various languages. You typically do not need to get overly picky with styling, but having rules in place will foster a cohesive feel for your applications, and aid in general maintenance.

The most important points on styling are:
- Your code should be easy to understand
- Comment complex logic, or better yet, rewrite it to be less cryptic.

Listed below are a few good style guides. You can mix and match these recommendations to meet your group collective aesthetic requirements.

- [SemanticUI CSS Style Guide](http://semantic-ui.com/guide/cssguide.html)
- [SemanticUI Language Style Guide](http://semantic-ui.com/guide/styleguide.html)
