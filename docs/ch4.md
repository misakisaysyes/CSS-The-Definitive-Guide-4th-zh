# 第 4 章 值和单位 Values and Units

In this chapter, we’ll tackle features that are the basis for almost everything you can do with CSS: the units that affect the colors, distances, and sizes of a whole host of properties, as well as the units that help to define those values. Without units, you couldn’t declare that an image should have 10 pixels of blank space around it, or that a heading’s text should be a certain size. By understanding the concepts put forth here, you’ll be able to learn and use the rest of CSS much more quickly.

## Keywords, Strings, and Other Text Values

Everything in a stylesheet is text, but there are certain value types that directly represent strings of text as opposed to, say, numbers or colors. Included in this category are URLs and, interestingly enough, images.

### Keywords

For those times when a value needs to be described with a word of some kind, there are keywords. A very common example is the keyword none, which is distinct from 0 (zero). Thus, to remove the underline from links in an HTML document, you would write:

```css
a:link, a:visited {text-decoration: none;}
```

Similarly, if you want to force underlines on the links, then you would use the keyword underline.

If a property accepts keywords, then its keywords will be defined only for the scope of that property. If two properties use the same word as a keyword, the behavior of the keyword for one property will not necessarily be shared with the other. As an example, normal, as defined for letter-spacing, means something very different than the normal defined for font-style.

### Global keywords

CSS3 defines three “global” keywords that are accepted by every property in the spec‐ ification: inherit, initial, and unset.

__inherit.__ The keyword inherit makes the value of a property on an element the same as the value of that property on its parent element. In other words, it forces inheritance to occur even in situations where it would not normally operate. In many cases, you don’t need to specify inheritance, since many properties inherit naturally. Nevertheless, inherit can still be very useful.

For example, consider the following styles and markup:

```html
#toolbar {background: blue; color: white;}

<div id="toolbar">
<a href="one.html">One</a> | <a href="two.html">Two</a> |
<a href="three.html">Three</a>
</div>
```

The div itself will have a blue background and a white foreground, but the links will be styled according to the browser’s preference settings. They’ll most likely end up as blue text on a blue background, with white vertical bars between them.

You could write a rule that explicitly sets the links in the “toolbar” to be white, but you can make things a little more robust by using inherit. You just add the following rule to the stylesheet:

```css
#toolbar a {color: inherit;}
```

This will cause the links to use the inherited value of color in place of the user agent’s default styles. Ordinarily, directly assigned styles override inherited styles, but inherit can undo that behavior. It might not always be a good idea—for example, here links might blend into surrounding text too much, and become an accessibility concern—but it can be done.

Similarly, you can pull a property value down from a parent even if it wouldn’t happen normally. Take border, for example, which is (rightfully) not inherited. If you want a span to inherit the border of its parent, all you need is span {border: inherit;}. More likely, though, you just want the border on a span to use the same border color as its parent. In that case span {border-color: inherit;} will do the trick.

__initial.__ The keyword initial sets the value of a property to the defined initial value, which in a way means it “resets” the value. For example, the default value of fontweight is normal. Thus, declaring font-weight: initial is the same as declaring font-weight: normal.

This might seem a little bit silly until you consider that not all values have explicitly defined initial values. For example, the initial value for color is “depends on user agent.” That’s not a funky keyword you should type! What it means is that the default value of color depends on things like the preferences settings in a browser. While almost nobody changes the default text color setting from black, someone might set it to a dark gray or even a bright red. By declaring color: initial;, you’re telling the browser to set the color of the element to whatever the user’s default color is set to be.

unset. The keyword unset acts as a universal stand-in for both inherit and initial. If the property is inherited, then unset has the same effect as if inherit was used. If the property is not inherited, then unset has the same effect as if initial was used.

<tips tips="orange">
As of late 2017, Opera Mini did not support any of initial, inherit, or unset. Internet Explorer did not support them through IE11.
</tips>

These global values are usable on all properties, but there is a special property that _only_ accepts the global keywords: __all__.

<cards cards="all"></cards>

all is a stand-in for all properties except direction and unicode-bidi. Thus, if you declare all: inherit on an element, you’re saying that you want all properties except direction and unicode-bidi to inherit their values from the element’s parent. Consider the following:

```html
section {color: white; background: black; font-weight: bold;}
#example {all: inherit;}
<section>
<div id="example">This is a div.</div>
</section>
```

You might think this causes the div element to inherit the values of color, back ground, and font-weight from the section element. And it does do that, yes—but it will also force inheritance of the values of every single other property in CSS (minus the two exceptions) from the section element.

Maybe that’s what you want, in which case, great. But if you just want to inherit the property values you wrote out for the section element, then the CSS would need to look more like this:

```css
section {color: white; background: black; font-weight: bold;}
#example {color: inherit; background: inherit; font-weight: inherit;}
```

Odds are what you really want in these situations is all: unset, but your stylesheet may vary.

<tips tips="blue">
As of late 2017, a new global keyword, revert, was being considered for adoption. Its goal was to allow rollbacks of values to those set by other origins—for example, to let an author say, “All property values for this element should be as if the author styles don’t exist, but user agent and user styles do.” Since it was still under consideration, it has not been documented in detail here.
</tips>

<tips tips="orange">
As of late 2017, Opera Mini and Microsoft Edge did not support
all. Support was under consideration for Edge.
</tips>

### String
A string value is an arbitrary sequence of characters wrapped in either single or double quotes, and is represented in value definitions with `<string>`. Two simple examples:

&emsp;"I like to play with strings."  
&emsp;'Strings are fun to play with.'

Note that the quotes balance, which is to say that you always start and end with the same kind of quotes. Getting this wrong can lead to all kinds of parsing problems, since starting with one kind of quote and trying to end with the other means the string won’t actually be terminated. You could accidentally incorporate subsequent rules into the string that way!

If you want to put quote marks inside strings, that’s OK, as long as they’re either not the kind you used to enclose the string or are escaped using a backslash:

&emsp;"I've always liked to play with strings."  
&emsp;'He said to me, "I like to play with strings."'  
&emsp;"It's been said that \"haste makes waste.\""  
&emsp;'There\'s never been a "string theory" that I\'ve liked.'

Note that the only acceptable string delimiters are ' and ", sometimes called “straight quotes.” That means you can’t use “curly” or “smart” quotes to begin or end a string value. You can use them inside a string value, as in this code example, though, and they don’t have to be escaped:

&emsp;"It’s been said that “haste makes waste.”"  
&emsp;'There’s never been a “string theory” that I’ve liked.'

This requires that you use Unicode encoding for your documents, but you should be doing that regardless. (You can find the Unicode standard at http://www.unicode.org/standard/standard.html.)

If you have some reason to include a newline in your string value, you can do that by escaping the newline itself. CSS will then remove it, making things as if it had never been there. Thus, the following two string values are identical from a CSS point of view:

&emsp;"This is the right place \  
&emsp;for a newline."  
&emsp;"This is the right place for a newline."

If, on the other hand, you actually want a string value that includes a newline character, then use the Unicode reference \A where you want the newline to occur:

&emsp;"This is a better place \Afor a newline."

### URLs

If you’ve written web pages, you’re almost certainly familiar with URLs (or, as in CSS2.1, URIs). Whenever you need to refer to one—as in the @import statement, which is used when importing an external stylesheet—the general format is:

&emsp;url(protocol://server/pathname)

This example defines what is known as an absolute URL. By absolute, I mean a URL that will work no matter where (or rather, in what page) it’s found, because it defines an absolute location in web space. Let’s say that you have a server called _web.waffles.org_. On that server, there is a directory called pix, and in this directory is an image _wafe22.gif_. In this case, the absolute URL of that image would be:  
&emsp;web.waffles.org/pix/waffle22.gif

This URL is valid no matter where it is found, whether the page that contains it is located on the server _web.wafes.org_ or _web.pancakes.com_. The other type of URL is a relative URL, so named because it specifies a location that is relative to the document that uses it. If you’re referring to a relative location, such as a file in the same directory as your web page, then the general format is:

&emsp;url(pathname)

This works only if the image is on the same server as the page that contains the URL. For argument’s sake, assume that you have a web page located at _http://web.wafes.org/syrup.html_ and that you want the image _wafe22.gif_ to appear on this page. In that case, the URL would be:

&emsp;pix/waffle22.gif

This path works because the web browser knows that it should start with the place it found the web document and then add the relative URL. In this case, the pathname _pix/wafe22.gif_ added to the server name _http://web.wafes.org_ equals _http://web.wafes.org/pix/wafe22.gif_. You can almost always use an absolute URL in place of a relative URL; it doesn’t matter which you use, as long as it defines a valid location.

In CSS, relative URLs are relative to the stylesheet itself, not to the HTML document that uses the stylesheet. For example, you may have an external stylesheet that imports another stylesheet. If you use a relative URL to import the second stylesheet, it must be relative to the first stylesheet.

As an example, consider an HTML document at _http://web.wafes.org/toppings/tips.html_, which has a link to the stylesheet _http://web.wafes.org/styles/basic.css_:

```html
<link rel="stylesheet" type="text/css"
href="http://web.waffles.org/styles/basic.css">
```

Inside the file basic.css is an @import statement referring to another stylesheet:

```css
@import url(special/toppings.css);
```

This __@import__ will cause the browser to look for the stylesheet at _http://web.wafes.org/styles/special/toppings.css_, not at _http://web.wafes.org/toppings/special/toppings.css_. If you have a stylesheet at the latter location, then the @import in basic.css should read one of the two following ways:

```css
@import url(http://web.waffles.org/toppings/special/toppings.css);
@import url(../special/toppings.css);
```

Note that there cannot be a space between the url and the opening parenthesis:


```css
body {background: url(http://www.pix.web/picture1.jpg);} /* correct */
body {background: url (images/picture2.jpg);} /* INCORRECT */
```

If the space is present, the entire declaration will be invalidated and thus ignored.


### Image
An image value is a reference to an image, as you might have guessed. Its syntax representation is `<image>`.

At the most basic level of support, which is to say the one every CSS engine on the planet would understand, an `<image>` value is a `<url>` value. In more advanced user agents, `<image>` stands for one of the following:

`<url>`  
A URL identifier of an external resource; in this case, the URL of an image.

`<image-set>`  
Perhaps unsurprisingly, a set of images, chosen based on a set of conditions embedded into the value. For example, an image-set() could specify that a larger image be used for desktop layouts, whereas a smaller image (both in pixel size and file size) be used for a mobile design. It is intended to at least approxi‐ mate the behavior of the srcset attribute for picture elements. As of late 2016, browser support for image-set was limited to Safari, Chrome, and desktop Opera, and was not on par with srcset’s full range of capabilities.

`<gradient>`  
Refers to either a linear or radial gradient image, either singly or in a repeating pattern. Gradients are fairly complex, and thus are covered in detail in Chapter 9.

### Identifiers

There are a few properties that accept an identifer value, which is a user-defined identifier of some kind; the most common example is generated list counters. They are represented in the value syntax as `<identifer>`. Identifiers themselves are words, and are case-sensitive; thus, myID and MyID are, as far as CSS is concerned, completely distinct and unrelated to each other. In cases where a property accepts both an identifier and one or more keywords, the author should take care to never define an identifier identical to a valid keyword.

## Numbers and Percentages

These value types are special because they serve as the foundation for so many other values types. For example, font sizes can be defined using the em identifier (covered later in this text) preceded by a number. But what kind of number? Defining the types of numbers here lets us speak clearly later on.

### Integers
An integer value is about as simple as it gets: one or more numbers, optionally prefixed by a + or − sign to indicate a positive or negative value. That’s it. Integer values are represented in value syntax as `<integer>`. Examples include 13, −42, 712, and 1,066.

Integer values that fall outside a defined range are, by default, considered invalid and cause the entire declaration to be ignored. However, some properties define behavior that causes values outside the accepted range to be set to the accepted value closest to the declared value, known as clamping. In cases (such as the property z-index) where there is no restricted range, user agents must support values up to ±1,073,741,824 (±230).

### Numbers

A number value is either an `<integer>` or a real number, which is to say an intege followed by a dot and then some number of following integers. Additionally, it can be prefixed by either + or − to indicate positive or negative values. Number values are represented in value syntax as `<number>`. Examples include 2.7183, −3.1416, and 6.2832.