### SWABATS
Intro to Web Design - Day 3

+ HTML - break up a page with divs
+ HTML - Understand how to use HTML5 semantic elements - header, footer, nav, etc.
+ HTML/CSS - Understand why and how we user Modernizer and Normalize to make sure our code is cross-browser compatible
+ CSS - Understand box model and how it is impacted by padding, margin and border
+ CSS - Understand cross-browser compatibility and how to use pre-fixes
+ CSS - Understand how to use box-sizing property to standardize the box-model across browsers
+ CSS - use content overflow property - visible, hidden, scroll, auto
+ CSS - understand inline vs. block vs. inline-block element displays
+ CSS - understand how to use float and clear properties
+ CSS - understand how to apply clearfix solution
+ CSS - understand how to use CSS position properties - relative, absolute and fixed


### Motivation
Yesterday we used CSS to style the fonts, images and backgrounds of our page. Today we’re going to learn how to use CSS to break up and arrange the content on our page.


### Lesson Plan 
+ We can break up a page with a generic sort of container called 

```ruby
<div></div>
```

We can add classes and ids to these divs to style them however we want. Adding ids and classes is the only way to differentiate these generic div containers.

+ HTML5 provides us with some helpful elements that we can use to break up our page and semantically describe what each section is being used for. These are:
	+ header
	+ footer
	+ nav
	+ aside
	+ section
	+ article
+ You’ll still need to apply styles to these items like:
	+ footer {
		+ background-color: purple;
		+ color: white;
		+ display:block;
		+ float: right;
}
+ But it is a little cleaner and saves you some time by eliminating the need to add a div with the class or ID footer.
+ Not all older browsers support these HTML5 semantic elements but luckily developers have already created a couple of good solutions to these problems.
+ These are:
+ Modernizr - a JavaScript library that detects HTML5 and CSS3 features in the user’s browser.
	+ http://modernizr.com/
	+ http://cdnjs.cloudflare.com/ajax/libs/modernizr/2.7.1/modernizr.min.js
	+ <script src="http://cdnjs.cloudflare.com/ajax/libs/modernizr/2.7.1/modernizr.min.js"></script>
+ and a Normalize css file:
	+ http://nicolasgallagher.com/about-normalize-css/
	+ http://cdnjs.cloudflare.com/ajax/libs/normalize/3.0.0/normalize.min.css
	+ <link rel="stylesheet" href="http://cdnjs.cloudflare.com/ajax/libs/normalize/3.0.0/normalize.min.css">
+ Older browsers also display unknown elements as inline. The following code is a CSS fix for FF, Safari, & Chrome that sets these elements to display block.
	+ article, aside, details, figcaption, figure, footer, header, hgroup, nav, section, summary { display: block; }
+ So how do we style these divs? You probably want to set your divs to a certain width and height.
+ There are several important elements that go into determining the total size of the div though. These include:
	+ margin - the space that you want between your divs
	+ border - you might want to include a bold border around your div
	+ padding - how much space you want between the edge of your div and the content inside your div
+ For instance - this is what your page might look like if you do not take these things into account: ***show a page with a couple of divs with zero margin, border and padding.***
+ These sizing attributes are part of something that we call the box model.

+ !!!!BOX MODEL IMAGE GOES HERE!!!!
+ Unfortunately, not all browsers treat these attributes the same. Most browsers follow the WC3 model but Internet Explorer is a rogue. Here are the two models:
+ !!!!!W3C box model image goes here!!!
+ !!!!!Internet Explorer box model goes here!!!

+ Luckily we have a box-sizing property that allows us to choose which model we want to follow. Here are the two options:
	+ /* IE model = border-box
+ W3C model = content-box */
+ You can choose which model you want to follow and set your CSS like this.
	+ div {
    	+ box-sizing: border-box;
	+ }
+ ***Demo how adding border, padding affects the total size of the div with each model. And have students create their own practice HTML document to try out this out - or maybe have them use jsfiddle like grover does?***
+ There are a few different methods that we can use to scale divs:
	+ Fixed (px)
	+ Elastic (em)
	+ Fluid (%)
	+ Using Min/Max Sizing
+ Each of these have their own pros and cons.
+ Fixed px (what we’ve been using) gives the developer a lot of control over what the user sees, but it is not flexible.
	+ No matter what size the screen is the div will be the same size - which means there might be a lot of white space on larger screens or the user might have to scroll when not all of the content fits on the page. 
+ Ems are a proportional unit of measure are most useful in sizing text in responsive web layouts. We’ll talk more about using ems to size text when we talk about responsive web design next week.
	+ In general 1em is equal 16px and here is a helpful site for conversions: http://pxtoem.com/ 
+ A fluid design uses percentages. So width and height can be set to take up a certain amount of the screen.
	+ This is a major part of creating a “responsive site”.
	+ We are going to take a lot more about responsive web design next week but in a nutshell - RWD is hugely important because people access web applications from a ton of different types of devices - from cell phones to giant wide screen desktop monitors and you want your website to look good on all of these devices. 
+ Another option is set min and max width and heights.
	+ This is a pretty good compromise in that it gives you more control over what the user sees, while also making the site flexible for multiple screen sizes.
	+ 960px is generally the max-width for a smaller screen and 1180px for a larger screen
	+ Note that setting the height of a div to 100% will only make it 100% as tall as its parent div. If you want it to take up 100% of the page, make sure that the parent div also has a height and min-height that is set to 100%.
+ ***Demo these things for students and have them practice/test.***
+ If you do not set a height for a div it will automatically be tall enough to fit the content. If you set a height you have a few options for how you display the content with the overflow property.
+ Demonstrate how each of these 
	+ div {
		+ overflow: visible | hidden | scroll | auto;
	+ }
+ looks and have students practice. http://jsfiddle.net/flatiron_school/sFfw5/
+ !!!!3 BLOCK DIAGRAM IMAGE GOES HERE!!!!

+ Another default for most browsers is to display divs,p,h in block style. That means that each element on the page will be displayed directly below the next one and take up the whole width of the page.
	+ displays one above the other, takes up the whole line. Able to specify width and top and bottom margin
	+ margins will overlap for block elements (above and below) but not for inline elements (horizontal)
+ There are a few other elements like spans and images which display inline - meaning they show up side by side. 
	+ appears side by side does not accept width or top and bottom margins
+ http://jsfiddle.net/flatiron_school/352A6/1/
+ We can change this by modifying the display property like this: 
	+ display: block;
	+ display: inline;
	+ display: inline-block;
+ !!!!DISPLAY BLOCK IMAGE!!!!!

+ That last one inline-block is sort of a combo of the other two - which seems like the best of both worlds - except here you can see that using inline-block doesn’t give us as much control - this element is kind of floating here instead of aligning at the top - display with jsfiddle. You can use inline-block just be aware of how it affects your layout.
+ By using the float property with display: block; you should have good control over how things are displayed on the page - including placement AND width/height + margins.
+ The float property accepts two values: right and left.
+ Demo how float works with three divs.
+ Float only affects elements after it. So we can leave this first div as block display and adding float: right to the second div will cause it to float to the right of the last div but still below the first one.
+ You may run into a situation where you are floating your elements and something like the footer is sneaking up to apl
+ !!!FOOTER TO APL IMAGE!!!!


+ To fix this you can add a clear property set to the value of both. This means clear divs floating both right and left and it will sink the footer to the bottom of the page.
+ One more thing to be aware of is collapsing parents.
+ If all of the divs inside of a parent are floating then the parent loses a reference for how big it should be. This often happens when you have a larger div like a wrapper - that might be controlling the width of the page - with floating divs - like articles inside. 
+ Demo an example. To solve this you can set up a clearfix class like this:
	+ .clearfix:after {
	+ content: ".";
   + display: block;
   + clear: both;
   + visibility: hidden;
   + height: 0;
   + line-height: 0;
}
+ Walk through the properties and values here.
+ We can also control the positioning of our divs more granularly with CSS positioning techniques like:
	+ Relative - will position a div relative to its parent
	+ Absolute - will position a div in absolute relation to the screen UNLESS it is within a div that is positioned in some way.
	+ Fixed - Will position the div at a fixed place on the page - even if the person scrolls down the fixed div will stay on their screen.
+ Let’s take a look at how this works with this example: http://jsfiddle.net/flatiron_school/rgyPC/1/.
+ One last thing you can control when it comes to positioning is the z-index which lets you layer divs and control their position into the third dimension!
+ Divs with a higher z-index will be positioned on top of elements with a lower z-index or no z index at all.
+ Here is an example:
+ .bluebox {
     + position: relative;
     + top: 125px;
     + left: 125px;
     + z-index: 3;
+ }
+ !!!!! Z INDEX IMAGE!!!!!

+ Let’s take a closer look with this jsfiddle: http://jsfiddle.net/flatiron_school/nWGts/ 
+ ***Now it’s time for you to apply your skills to your personal page!***


### Conclusion 

### Hints/Hurdles