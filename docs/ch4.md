# 第 4 章 值和单位 Values and Units

In this chapter, we’ll tackle features that are the basis for almost everything you can do with CSS: the units that affect the colors, distances, and sizes of a whole host of properties, as well as the units that help to define those values. Without units, you couldn’t declare that an image should have 10 pixels of blank space around it, or that a heading’s text should be a certain size. By understanding the concepts  put forth here, you’ll be able to learn and use the rest of CSS much more quickly.

> 在本章中，我们将介绍大部分你会用到的CSS中的基础特性，例如：影响属性颜色，距离和大小的单位，以及有助于定义这些属性值的单位。没有单位，您将无法声明图像周围应有10像素的空白，或者标题的文本应具有一定的大小。 通过理解此处提出的概念，您将能够更快地学习和使用其余的CSS。

## Keywords, Strings, and Other Text Values

Everything in a stylesheet is text, but there are certain value types that directly represent strings of text as opposed to, say, numbers or colors. Included in this category are URLs and, interestingly enough, images.

> 样式表中的所有内容都是文本，但是某些值类型可以直接表示文本字符串，而不是数字或颜色。 URL就是其中一种，有趣的是，图像也在其中。

### Keywords

For those times when a value needs to be described with a word of some kind, there are keywords. A very common example is the keyword none, which is distinct from 0 (zero). Thus, to remove the underline from links in an HTML document, you would write:

> 对于需要用某种单词来描述值的时候，会用到一些关键词。 一个非常常见的示例是关键字none，它不同于0（零）。 因此，要从HTML文档的链接中删除下划线，写法如下：

```css
a:link, a:visited {text-decoration: none;}
```

Similarly, if you want to force underlines on the links, then you would use the keyword underline.

> 相似地，如果你想给链接加上下划线，你可以使用下划线关键字。

If a property accepts keywords, then its keywords will be defined only for the scope of that property. If two properties use the same word as a keyword, the behavior of the keyword for one property will not necessarily be shared with the other. As an example, normal, as defined for letter-spacing, means something very different than the normal defined for font-style.

> 如果某个属性接受关键字，那么它接受的关键字要在该属性的定义范围内。如果两个不同的属性都接受一个相同单词的关键词，一个属性的行为与另一个属性的行为不一定表现相同。例如，normal关键字用在letter-spacing与用在font-style上表示不同的定义。

### Global keywords

CSS3 defines three “global” keywords that are accepted by every property in the specification: inherit, initial, and unset.

> CSS3定义了三个“全局”的关键词：inherit, initial和unset。这三个关键词可以用在任何属性上。

__inherit.__ The keyword inherit makes the value of a property on an element the same as the value of that property on its parent element. In other words, it forces inheritance to occur even in situations where it would not normally operate. In many cases, you don’t need to specify inheritance, since many properties inherit naturally. Nevertheless, inherit can still be very useful.

> __inherit__ 关键词使元素上该属性的值继承其父元素响应属性的值。换句话来说，在继承没有发生的情况下，它会强行进行属性继承。在很多情况下，你不需要特意指明继承，很多继承是自动进行的。但是，inherit关键词还是非常有用的。

For example, consider the following styles and markup:

> 例如下面的例子：

```html
#toolbar {background: blue; color: white;}

<div id="toolbar">
<a href="one.html">One</a> | <a href="two.html">Two</a> |
<a href="three.html">Three</a>
</div>
```

The div itself will have a blue background and a white foreground, but the links will be styled according to the browser’s preference settings. They’ll most likely end up as blue text on a blue background, with white vertical bars between them.

> div元素本身带有蓝色背景和白色前景，而链接的样式会根据浏览器的设置变化。链接最终大部分是以蓝色背景及蓝色文字的效果呈现，而且两边会有一条白色的竖线。

You could write a rule that explicitly sets the links in the “toolbar” to be white, but you can make things a little more robust by using inherit. You just add the following rule to the stylesheet:

> 你可以定义一条新的规则使“toolbar”中的链接变成白色。不过通过继承来做的话会使代码更加健壮，你只需要在样式表中添加下面这条规则：

```css
#toolbar a {color: inherit;}
```

This will cause the links to use the inherited value of color in place of the user agent’s default styles. Ordinarily, directly assigned styles override inherited styles, but inherit can undo that behavior. It might not always be a good idea—for example, here links might blend into surrounding text too much, and become an accessibility concern—but it can be done.

> 这将导致链接使用集成的color属性值覆盖用户代理默认样式。通常，这样直接分配的样式会覆盖掉继承的样式，但是inherit关键词可以取消这种覆盖。这可能不是一个好做法，因为这样有可能使链接混入到周围的文本中，而且会引起前面说过的可访问性问题。但是这样做确实可以满足上面的要求。

Similarly, you can pull a property value down from a parent even if it wouldn’t happen normally. Take border, for example, which is (rightfully) not inherited. If you want a span to inherit the border of its parent, all you need is span {border: inherit;}. More likely, though, you just want the border on a span to use the same border color as its parent. In that case span {border-color: inherit;} will do the trick.

> 相似地，你想让一个属性值继承，而这个属性的继承是不会自动发生。举个例子，border属性不会自动继承父元素。如果你想让某个span的border属性继承父元素，你所需做的仅仅是添加一条```span{border: inherit;}```。大多数情况下，你想要的只是继承父元素的边框颜色，```span{border-color: inherit;}```足以解决问题。

__initial.__ The keyword initial sets the value of a property to the defined initial value, which in a way means it “resets” the value. For example, the default value of fontweight is normal. Thus, declaring font-weight: initial is the same as declaring font-weight: normal.

> __initial__ 关键词可以将属性的值恢复成初始值，某种程度上可以说它“重置”了该值。例如：fontweight属性的默认值为normal。因此，```font-weight: initial```这样声明跟```font-weight: normal```这样声明是一个效果。

This might seem a little bit silly until you consider that not all values have explicitly defined initial values. For example, the initial value for color is “depends on user agent.” That’s not a funky keyword you should type! What it means is that the default value of color depends on things like the preferences settings in a browser. While almost nobody changes the default text color setting from black, someone might set it to a dark gray or even a bright red. By declaring color: initial;, you’re telling the browser to set the color of the element to whatever the user’s default color is set to be.

> 如果所有的属性都有明确的初始值，你会觉得这个关键词的设计有点愚蠢，但事实并不是这样的。举个例子，字体颜色的初始值是由用户代理来决定的，而不是你设置的某种时髦字体。这意味着字体颜色的默认值是由浏览器的偏好设置决定的。虽然大部分用户的文本设置是黑色字体，也有一部分用户将字体设置成灰色甚至是亮红色。通过声明```color: initial;```,你可以告诉浏览器将元素内的字体颜色更改成用户设置的默认值。

__unset.__ The keyword unset acts as a universal stand-in for both inherit and initial. If the property is inherited, then unset has the same effect as if inherit was used. If the property is not inherited, then unset has the same effect as if initial was used.

> __unset__ 关键词是inherit和initial的通用替代。如果一个属性是继承的，unset的效果跟inherit关键词的效果相同，如果一个属性不是继承的，unset的效果则跟initial关键词的效果相同。

<tips tips="orange">
As of late 2017, Opera Mini did not support any of initial, inherit, or unset. Internet Explorer did not support them through IE11.
</tips>

These global values are usable on all properties, but there is a special property that _only_ accepts the global keywords: __all__.

> 这些全局关键词可以在任何属性上使用，但有一个特殊的属性: __all__,它只能接受全局关键词。

<cards cards="all"></cards>

__all__ is a stand-in for all properties except direction and unicode-bidi. Thus, if you declare all: inherit on an element, you’re saying that you want all properties except direction and unicode-bidi to inherit their values from the element’s parent. Consider the following:

> __all__ 关键词用于指代全部属性，除direction、unicode-bidi。因此，如果你在一个元素中这样声明```all: inherit```，意思是除了direction、unicode-bidi属性外，全部属性的值均继承自它们的父元素。如下：

```html
section {color: white; background: black; font-weight: bold;}
#example {all: inherit;}
<section>
<div id="example">This is a div.</div>
</section>
```

You might think this causes the div element to inherit the values of color, background, and font-weight from the section element. And it does do that, yes—but it will also force inheritance of the values of every single other property in CSS (minus the two exceptions) from the section element.

> 你或许会认为这会让div元素的字体颜色、背景及字体大小的值都继承自section元素。事实上确实是这样的，它会强制从section元素继承CSS所有的属性值（除了那两个特殊的属性）。

Maybe that’s what you want, in which case, great. But if you just want to inherit the property values you wrote out for the section element, then the CSS would need to look more like this:

> 在某种情况下，你或许想要的就是这种效果，这样做很完美。但是如果你想继承section元素中已编写的属性，你需要像下面这样编写CSS：

```css
section {color: white; background: black; font-weight: bold;}
#example {color: inherit; background: inherit; font-weight: inherit;}
```

Odds are what you really want in these situations is all: unset, but your stylesheet may vary.

> 在这种情况在你真正需要设置的是`all: unset`，但这在不同的样式表中会有不同的效果。

<tips tips="blue">
As of late 2017, a new global keyword, revert, was being considered for adoption. Its goal was to allow rollbacks of values to those set by other origins—for example, to let an author say, “All property values for this element should be as if the author styles don’t exist, but user agent and user styles do.” Since it was still under consideration, it has not been documented in detail here.
</tips>

<tips tips="orange">
As of late 2017, Opera Mini and Microsoft Edge did not support all. Support was under consideration for Edge.
</tips>

### String
A string value is an arbitrary sequence of characters wrapped in either single or double quotes, and is represented in value definitions with `<string>`. Two simple examples:

> 字符串值是用单引号或双引号引起来的任意字符序列，并在值定义中用`<string>`表示。 两个简单的例子：

&emsp;"I like to play with strings."  
&emsp;'Strings are fun to play with.'

Note that the quotes balance, which is to say that you always start and end with the same kind of quotes. Getting this wrong can lead to all kinds of parsing problems, since starting with one kind of quote and trying to end with the other means the string won’t actually be terminated. You could accidentally incorporate subsequent rules into the string that way!

> 请务必注意引号必须以相同类型的引号作闭合。如果你开头用了一种引号，闭合时用了另一种引号，将会导致出现各种解析问题。甚至可能会将你后续定义的规则合并到这个字符串当中。

If you want to put quote marks inside strings, that’s OK, as long as they’re either not the kind you used to enclose the string or are escaped using a backslash:

> 如果你的字符串中包含引号，不是用来开头或闭合的那些，用反斜杠来进行转义即可。

&emsp;"I've always liked to play with strings."  
&emsp;'He said to me, "I like to play with strings."'  
&emsp;"It's been said that \"haste makes waste.\""  
&emsp;'There\'s never been a "string theory" that I\'ve liked.'

Note that the only acceptable string delimiters are ' and ", sometimes called “straight quotes.” That means you can’t use “curly” or “smart” quotes to begin or end a string value. You can use them inside a string value, as in this code example, though, and they don’t have to be escaped:

> 注意只有'和"能用作边界符，这两个符号又叫“straight quotes”。这意味着你不能用“curly quotes”和“smart quotes”去开始或结束一个字符串，同时这也意味着如果你的字符串中包含这两种引号，你可以直接使用，不需要进行转义。

&emsp;"It’s been said that “haste makes waste.”"  
&emsp;'There’s never been a “string theory” that I’ve liked.'

This requires that you use Unicode encoding for your documents, but you should be doing that regardless. (You can find the Unicode standard at http://www.unicode.org/standard/standard.html.)


If you have some reason to include a newline in your string value, you can do that by escaping the newline itself. CSS will then remove it, making things as if it had never been there. Thus, the following two string values are identical from a CSS point of view:

> 如果出于某些原因，你需要在字符串中插入换行符，可以通过转义字符来实现。然后，CSS会删除它，就好像它没有出现过一样。所以从CSS的角度来看，下面两种写法是一致的。

&emsp;"This is the right place \  
&emsp;for a newline."  
&emsp;"This is the right place for a newline."

If, on the other hand, you actually want a string value that includes a newline character, then use the Unicode reference \A where you want the newline to occur:

> 相反，如果你确实是想在字符串中插入一个换行符，你只需要用`\A`实现换行：

&emsp;"This is a better place \Afor a newline."

### URLs

If you’ve written web pages, you’re almost certainly familiar with URLs (or, as in CSS2.1, URIs). Whenever you need to refer to one—as in the @import statement, which is used when importing an external stylesheet—the general format is:

> 如果你写过网页，那么你肯定对URLs很熟悉（或者是CSS2.1中的URIs）。当你需要引用一个url时（如同在导入外部样式表时使用@import语句），一般格式为：

&emsp;url(protocol://server/pathname)

This example defines what is known as an absolute URL. By absolute, I mean a URL that will work no matter where (or rather, in what page) it’s found, because it defines an absolute location in web space. Let’s say that you have a server called _web.waffles.org_. On that server, there is a directory called pix, and in this directory is an image _wafe22.gif_. In this case, the absolute URL of that image would be: 

> 上面的例子用到的是我们熟知的绝对地址。使用绝对地址的话，无论在当前页面还是别的页面，这个URL都会正常工作，因为绝对地址定义的是资源在网络中的绝对位置。举个例子，如果你有个叫 _web.waffles.org_ 的服务器。在这个服务器上，有一个pix的路径，在这个路径上有一个叫 _wafe22.gif_ 的图像资源。这种情况下，这个图像资源的绝对地址如下：

&emsp;web.waffles.org/pix/waffle22.gif

This URL is valid no matter where it is found, whether the page that contains it is located on the server _web.wafes.org_ or _web.pancakes.com_. The other type of URL is a relative URL, so named because it specifies a location that is relative to the document that uses it. If you’re referring to a relative location, such as a file in the same directory as your web page, then the general format is:

> 这个URL无论页面是在 _web.wafes.org_ 还是 _web.pancakes.com_ 服务器下，它总是有效的。另一种类型的URL是相对地址，从命名得知该地址用于表示与当前页面文档有相对关系的地址。如果你要指向一个相对地址，例如与网页同一目录下的一个文件，则一般格式为：

&emsp;url(pathname)

This works only if the image is on the same server as the page that contains the URL. For argument’s sake, assume that you have a web page located at _http://web.wafes.org/syrup.html_ and that you want the image _wafe22.gif_ to appear on this page. In that case, the URL would be:

> 只有当图像和URL的页面在同一服务器上时，这个方法才有效。为了做比较论证，假设你现在有一个网页，地址为 _http://web.wafes.org/syrup.html_ ，和一个出现在这个页面上的图像 _wafe22.gif_ 。这种情况下，URL是这样的：

&emsp;pix/waffle22.gif

This path works because the web browser knows that it should start with the place it found the web document and then add the relative URL. In this case, the pathname _pix/wafe22.gif_ added to the server name _http://web.wafes.org_ equals _http://web.wafes.org/pix/wafe22.gif_. You can almost always use an absolute URL in place of a relative URL; it doesn’t matter which you use, as long as it defines a valid location.

> 这个路径会生效，因为浏览器知道应该用文档所在的地址拼接上相对地址。在这种情况下，路径 _pix/wafe22.gif_ 被拼接到服务器 _http://web.wafes.org_ 后形成 _http://web.wafes.org/pix/wafe22.gif_ 。你可以在大部分地方用绝对地址来代替相对地址。只要最终能形成一个有效地址，无论哪种形式都可以。

In CSS, relative URLs are relative to the stylesheet itself, not to the HTML document that uses the stylesheet. For example, you may have an external stylesheet that imports another stylesheet. If you use a relative URL to import the second stylesheet, it must be relative to the first stylesheet.

> 在CSS中，相对地址是相对于样式表自身的，而不是HTML文档。例如，如果你的文档中引入了一个外部样式表，这个外部样式表中又以相对位置引入了另一个外部样式表，第二个样式表必须在第一个样式表的相对位置。

As an example, consider an HTML document at _http://web.wafes.org/toppings/tips.html_, which has a link to the stylesheet _http://web.wafes.org/styles/basic.css_:

> 举个例子，如果一个位置为 _http://web.wafes.org/toppings/tips.html_ 的HTML文档，里面引入了一个样式表，位置为 _http://web.wafes.org/styles/basic.css_ ：

```html
<link rel="stylesheet" type="text/css"
href="http://web.waffles.org/styles/basic.css">
```

Inside the file `basic.css` is an `@import` statement referring to another stylesheet:

> 如果在文件`basic.css`内引入另一个样式表的话，使用的是`@import`语句：

```css
@import url(special/toppings.css);
```

This __@import__ will cause the browser to look for the stylesheet at _http://web.wafes.org/styles/special/toppings.css_, not at _http://web.wafes.org/toppings/special/toppings.css_. If you have a stylesheet at the latter location, then the @import in basic.css should read one of the two following ways:

> __@import__ 语句会使浏览器去寻找 _http://web.wafes.org/styles/special/toppings.css_ ，而不是 _http://web.wafes.org/toppings/special/toppings.css_ 。如果你要引入后面那个样式表，那么在`basic.css`中的`@import`应该这样写：

```css
@import url(http://web.waffles.org/toppings/special/toppings.css);
@import url(../special/toppings.css);
```

Note that there cannot be a space between the url and the opening parenthesis:

> 注意URL与括号之间不能有空格。

```css
body {background: url(http://www.pix.web/picture1.jpg);} /* correct */
body {background: url (images/picture2.jpg);} /* INCORRECT */
```

If the space is present, the entire declaration will be invalidated and thus ignored.

> 如果存在空格，那么整个声明都会不合法并失效。

### Image
An image value is a reference to an image, as you might have guessed. Its syntax representation is `<image>`.

> 您可能已经猜到，图像值是对图像的引用。 它的语法表示为`<image>`。

At the most basic level of support, which is to say the one every CSS engine on the planet would understand, an `<image>` value is a `<url>` value. In more advanced user agents, `<image>` stands for one of the following:

> 大部分的CSS解析器的最基础功能都能做到把一个`<image>`的值当成和`<url>`一样。在部分更为先进的用户代理中，`<image>`代表以下其中一种：

`<url>`  
A URL identifier of an external resource; in this case, the URL of an image.

> 一个外部资源的地址标识符；在这里，指的是图像的URL。

`<image-set>`  
Perhaps unsurprisingly, a set of images, chosen based on a set of conditions embedded into the value. For example, an image-set() could specify that a larger image be used for desktop layouts, whereas a smaller image (both in pixel size and file size) be used for a mobile design. It is intended to at least approximate the behavior of the srcset attribute for picture elements. As of late 2016, browser support for image-set was limited to Safari, Chrome, and desktop Opera, and was not on par with srcset’s full range of capabilities.

> 也许不足为奇的是，根据嵌入值中的一组条件选择一组图像。 例如，image-set（）可以指定将较大的图像用于桌面布局，而将较小的图像（像素大小和文件大小）用于移动设计。 它旨在至少近似于图片元素的srcset属性的行为。 截至2016年底，浏览器对图像集的支持仅限于Safari，Chrome和桌面Opera，并且无法与srcset的全部功能相提并论。

`<gradient>`  
Refers to either a linear or radial gradient image, either singly or in a repeating pattern. Gradients are fairly complex, and thus are covered in detail in Chapter 9.

> 单独或重复地引用线性或径向渐变图像。渐变相当复杂，因此在第9章中将对其进行详细介绍。

### Identifiers

There are a few properties that accept an identifer value, which is a user-defined identifier of some kind; the most common example is generated list counters. They are represented in the value syntax as `<identifer>`. Identifiers themselves are words, and are case-sensitive; thus, myID and MyID are, as far as CSS is concerned, completely distinct and unrelated to each other. In cases where a property accepts both an identifier and one or more keywords, the author should take care to never define an identifier identical to a valid keyword.

> 部分属性可以接收一个标识符值，它是用户自己定义的某种标识符。最常见的例子是生成列表计数器。它们在值语法中表示为`<identifer>`。 标识符本身就是单词，并且区分大小写；因此，就CSS而言，myID和MyID完全不同且彼此无关。如果某个属性同时接受标识符和一个或多个关键字，则作者应注意不要定义与有效关键字相同的标识符。

## Numbers and Percentages

These value types are special because they serve as the foundation for so many other values types. For example, font sizes can be defined using the em identifier (covered later in this text) preceded by a number. But what kind of number? Defining the types of numbers here lets us speak clearly later on.

> 这些值类型很特殊，因为它们是许多其他值类型的基础。例如，可以使用em标识符（在本文的后面介绍）加上数字来定义字体大小。但是是什么样的数字呢？在这里定义数字的类型我们稍后再详细分析。

### Integers
An integer value is about as simple as it gets: one or more numbers, optionally prefixed by a + or − sign to indicate a positive or negative value. That’s it. Integer values are represented in value syntax as `<integer>`. Examples include 13, −42, 712, and 1,066.

> 整数值就简单多了：一个或多个数字，可以选择在其前面加上+或-号来表示正值或负值。整数值在值语法中表示为`<integer>`。 示例包括13，-42、712和1,066。

Integer values that fall outside a defined range are, by default, considered invalid and cause the entire declaration to be ignored. However, some properties define behavior that causes values outside the accepted range to be set to the accepted value closest to the declared value, known as clamping. In cases (such as the property z-index) where there is no restricted range, user agents must support values up to ±1,073,741,824 (±230).

> 默认情况下，超出定义范围的整数值被视为无效，并导致整个声明被忽略。但是，某些属性定义的行为会导致将超出可接受范围的值设置为最接近声明值的可接受值，称为钳位。 在没有限制范围的情况下（例如z-index属性），用户代理必须支持最大±1,073,741,824（±230）的值。

### Numbers

A number value is either an `<integer>` or a real number, which is to say an intege followed by a dot and then some number of following integers. Additionally, it can be prefixed by either + or − to indicate positive or negative values. Number values are represented in value syntax as `<number>`. Examples include 2.7183, −3.1416, and 6.2832.

> 一个数字值可以是一个`<integer>`或一个实数，即一个整数，后跟一个点，然后是一些随后的整数。另外，可以在其前面加上+或-表示正值或负值。数字值在值语法中表示为`<number>`。示例包括2.7183，-3.1416和6.2832