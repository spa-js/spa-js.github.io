---
layout: default
title: Development - CSS
category: bp
---



# CSS Development

## General Best Practices

- Use a reset CSS base line like [Normalize CSS](http://necolas.github.io/normalize.css/) to ensureconsstent styling across all browsers. Most theme-able toolkits also provide normalization.

- Your CSS should contain a rule that applies “display:block” to the HTML5 elements you use:
	- ie. `header,hgroup,nav,section,article,aside,footer { display:block; }`
	- Normalization CSS should do this for you

- Use percentages for layouts, not pixels
	- Key to responsive design.
	- When paired with media queries, serves as a foundation for “Mobile First” design
	- ie. `titleSection { height: 10%; }`

- Use relative font sizes, not fixed pixel sizes
	- Helps in responsive and accessibility
	- Good: `h1 { text-size: 1.25em; }`
	- Bad: `h1 { text-size: 24px; }`

- Use CSS3 features where possible, instead of images or javascript
	- Improved performance
	- Less images to download/process
	- Proper separation of concerns (CSS for styling, JavaScript for logic)

### General References
- [Best Practices for a Faster Web App with HTML5](http://www.html5rocks.com/en/tutorials/speed/quick/)
- [HTML5 Best Practices for Designers](http://www.instantshift.com/2012/03/27/html5-best-practices-for-designers/)
- [HTML5 Essentials with Best Practices](http://webrevisions.com/tutorials/html5-essentials-with-best-practices/#.UYu3QiuDTmF)


## Responsive Web Design

Responsive web design has been a hot topic of late. Effectively, it means that the app responds sensibly to sizing and rotation events.

For desktops, it does look cool to have everything re-flow dynamically when you change the browser's width, but I've always considered that as eye-candy more than proper functionality. It has its place, but most users are not whipping the browser size around all that often. Don't go overboard with dynamic resizing. Adapt your primary page on app startup and make "functional only" changes should the user change the browser size. The rest is just "wow" factor for demos.

For mobile devices, there is a different use case. Since mobile web and hybrid apps are always full screen, there are effectively two possible form factors or sizes; phone (small) and tablet (large), and two orientations; portrait and landscape. Your app should reasonably support both form factors. For tablets, you either provide more details on each view, or maintain a constant navigation section. Orientation changes can be handled either by simply resizing the page and allowing scrolling to happen naturally, or by re-organization of the layout (such as moving navigation from the top to the left). Both are reasonable solutions, but are dependent on the apps overall visual design requirements.

- [HTML5 And CSS3 Responsive Web Design Cookbook](http://www.creativealys.com/2013/09/27/html5-and-css3-responsive-web-design-cookbook/) - A comprehensive free ebook that details various responsive techniques


## Proper layouts using Flexbox

Flexbox is a revolution in clean CSS based layout. Yes, I'm talking to all of you that are still using `<table>` tags or layout, which while a simple cheat, has been a major no-no for years. The only alternatives for layout were either a nightmare of floating and positioned divs, or some 3rd party CSS library like [Bootstrap](http://getbootstrap.com/). There is finally a standards based and easy to use (honest!) solution. It is supported by all major browers, with the downside of IE where support starts with version 10.

- [A complete guide to Flexbox](http://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [A showcase of traditionally hard CSS problems, easily solved using flexbox](http://philipwalton.github.com/solved-by-flexbox)


## Using CSS Preprocessors

Preprocessors extend the standard CSS language with custom logic and variables. This enables you to define a cusotm color set and use variables throughout your CSS files to use those colors. For large and complex projects, this can be very advantageous.

There are several popular preprocessors implementations:
- [Sass](http://sass-lang.com/)
- [LESS](http://lesscss.org/)
- [Stylus](http://learnboost.github.io/stylus/)

The big concern when using preprocessors is that you must implement a new build process to manage them. Most allow for runtime processing which performs the conversion on the fly and is valuable during development. But, this is an anti-pattern post-development, as it has a negative impact on startup time.

### Resources:
- [CSS Processors compared](http://abhisharma.co.in/#sassvsless)



## Style Guides

Your company should adopt a standard style guide for coding in various languages. You typically do not need to get overly picky with styling, but having rules in place will foster a cohesive feel for your applications, and aid in general maintenance.

The most important points on styling are:
- Your code should be easy to understand
- Comment complex logic, or better yet, rewrite it to be less cryptic.

Listed below are a few good style guides. You can mix and match these recommendations to meet your group collective aesthetic requirements.

- [SemanticUI CSS Style Guide](http://semantic-ui.com/guide/cssguide.html)
- [SemanticUI Language Style Guide](http://semantic-ui.com/guide/styleguide.html)
