# 第 9 章 颜色、背景和渐变 Colors, Backgrounds, and Gradients

Remember the first time you changed the colors of a web page? Instead of the default black text on a white background with blue links, all of a sudden you could use any combination of colors you desired—perhaps light blue text on a black background with lime green hyperlinks. From there, it was just a short hop to colored text and, eventually, even to multiple colors for the text in a page. Once you could add background images, too, just about anything became possible, or so it seemed. Cascading Style Sheets (CSS) takes color and backgrounds even further, letting you apply many different colors and backgrounds to a single page or element, and even apply multiple backgrounds to the same element.

> 还记得你第一次改变网页的颜色吗?突然之间，你可以使用任何你想要的颜色组合来代替白色背景上的默认黑色文本和蓝色链接，比如在黑色背景上的淡蓝色文本和石灰绿色的超链接。从这里到彩色文本只是一个短暂的跳跃，最终，甚至到一个页面中的文本的多种颜色。一旦你可以添加背景图片，几乎任何事情都成为可能，至少看起来是这样。层叠样式表(CSS)可以进一步处理颜色和背景，让您可以将许多不同的颜色和背景应用于单个页面或元素，甚至可以将多个背景应用于同一元素。

## 9.1 Colors

When you’re designing a page, you need to plan it out before you start. That’s generally true in any case, but with colors, it’s even more so. If you’re going to make all hyperlinks yellow, will that clash with the background color in any part of your document? If you use too many colors, will the user be too overwhelmed? (Hint: yes.) If you change the default hyperlink colors, will users still be able to figure out where your links are? (For example, if you make both regular text and hyperlink text the same color, it will be much harder to spot links—in fact, almost impossible if the links aren’t underlined.)

> 当你在设计一个页面时，你需要在开始之前就做好计划。这在任何情况下都是正确的，但是对于颜色，更是如此。如果你要把所有的超链接都变成黄色，这会与你文档的任何部分的背景色冲突吗?如果你使用了太多的颜色，用户会被淹没吗?(提示:是的。)如果你改变了默认的超链接颜色，用户还能知道你的链接在哪里吗?(例如，如果将普通文本和超链接文本都设置为相同的颜色，则很难发现链接—实际上，如果链接没有下划线，几乎是不可能的。)

In CSS, you can set both the foreground and background colors of any element. In order to understand how this works, it’s important to understand what’s in the foreground of an element and what isn’t. Generally speaking, it’s the text of an element, although the foreground also includes the borders around the element. Thus, there are two ways to directly affect the foreground color of an element: by using the color property, and by setting the border colors using one of a number of border properties.

> 在 CSS 中，你可以设置任何元素的前景和背景颜色。为了理解这是如何工作的，重要的是要理解元素的前景中有什么，而不是什么。一般来说，它是元素的文本，尽管前景也包括元素周围的边框。因此，有两种方法可以直接影响元素的前景色:一种是使用 color 属性，另一种是使用边框属性设置边框颜色。

### 9.1.1 Foreground Colors

The easiest way to set the foreground color of an element is with the property color.

<Cards cards="color" />

This property accepts as a value any valid color type, such as `#FFCC00` or `rgba(100%,80%,0%,0.5)`.

> 此属性接受任何有效颜色类型的值，如' #FFCC00 '或' rgba(100%，80%，0%，0.5) '。

For nonreplaced elements like paragraphs or `em` elements, `color` sets the color of the text in the element, as illustrated in Figure 9-1, which is the result of the following code:

> 对于段落或' em '元素等不可替换的元素，' color '设置元素中文本的颜色，如图 9-1 所示，这是以下代码的结果:

```html
<p style="color: gray;">This paragraph has a gray foreground.</p>
<p>This paragraph has the default foreground.</p>
```

<Figures figure="9-1">Declared color versus default color</Figures>

In Figure 9-1, the default foreground color is black. That doesn’t have to be the case, since the user might have set her browser (or other user agent) to use a different foreground (text) color. If the browser’s default text color was set to `green`, the second paragraph in the preceding example would be green, not black—but the first paragraph would still be gray.

> 在图 9-1 中，默认的前景色是黑色。这不是必须的，因为用户可能已经将其浏览器(或其他用户代理)设置为使用不同的前景(文本)颜色。如果浏览器的默认文本颜色设置为“绿色”，那么前面示例中的第二段将是绿色的，而不是黑色的——但是第一段仍然是灰色的。

You need not restrict yourself to such basic operations. There are plenty of ways to use `color`. You might have some paragraphs that contain text warning the user of a potential problem. In order to make this text stand out more than usual, you might decide to color it red. Just apply a class of `warn` to each paragraph that contains warning text (`<p class="warn">`) and the following rule:

> 你不必局限于这些基本的操作。“color”有很多种用法。您可能有一些段落包含警告用户潜在问题的文本。为了使这段文字比平常更突出，你可以决定把它涂成红色。只需对每个包含警告文本(`<p class="warn">`)和以下规则的段落应用' warn '类:

```css
p.warn {
  color: red;
}
```

In the same document, you might decide that any unvisited hyperlinks within a warning paragraph should be green:

> 在同一份文件中，你可能会决定警告段落中任何未被访问的超链接都应该是绿色的:

```css
p.warn {
  color: red;
}
p.warn a:link {
  color: green;
}
```

Then you change your mind, deciding that warning text should be dark red, and that unvisited links in such text should be medium purple. The preceding rules need only be changed to reflect the new values, as illustrated in Figure 9-2, which is the result of the following code:

> 然后，您改变了主意，决定警告文本应该是深红色，未访问的链接应该是中紫色。前面的规则只需要改变以反映新的值，如图 9-2 所示，这是以下代码的结果:

```css
p.warn {
  color: #600;
}
p.warn a:link {
  color: #400040;
}
```

<Figures figure="9-2">Changing colors</Figures>

Another use for `color` is to draw attention to certain types of text. For example, boldfaced text is already fairly obvious, but you could give it a different color to make it stand out even further—let’s say, maroon:

> “color”的另一个用法是将注意力吸引到特定类型的文本上。例如，粗体字已经很明显了，但是你可以给它一个不同的颜色，让它更加突出——比如说，栗色:

```css
b,
strong {
  color: maroon;
}
```

Then you decide that you want all table cells with a class of `highlight` to contain light yellow text:

> 然后你决定你想要的所有表格单元格类'高亮'包含淡黄色文本:

```css
td.highlight {
  color: #ff9;
}
```

If you don’t set a background color for any of your text, you run the risk that a user’s setup won’t combine well with your own. For example, if a user has set his browser’s background to be a pale yellow, like `#FFC`, then the previous rule would generate light yellow text on a pale yellow background. Far more likely is that it’s still the default background of white, against which light yellow is still going to be hard to read. It’s therefore generally a good idea to set foreground and background colors together. (We’ll talk about background colors very shortly.)

> 如果您不为任何文本设置背景颜色，您将面临用户的设置无法与您自己的设置很好地结合的风险。例如，如果用户将浏览器的背景设置为淡黄色，比如' #FFC '，那么前面的规则将在淡黄色背景上生成淡黄色文本。更有可能的是，它仍然是白色的默认背景，在这种背景下，淡黄色仍然很难阅读。因此，将前景和背景颜色设置在一起通常是一个好主意。(我们很快会讲到背景色。)

### 9.1.2 Affecting Borders

The value of `color` can also affect the borders around an element. Let’s assume you’ve declared these styles, which have the result shown in Figure 9-3. This is the result of the following code:

> “color”的值也会影响元素周围的边框。假设您已经声明了这些样式，其结果如图 9-3 所示。这是以下代码的结果:

```css
p.aside {
  color: gray;
  border-style: solid;
}
```

<Figures figure="9-3">Border colors are taken from the content’s color</Figures>

The element `<p class="aside">` has gray text and a gray medium-width solid border. This is because the foreground color is applied to the borders by default. Should you desire, you can override this with the property `border-color`:

> 元素 `<p class="aside">` 有灰色文本和灰色的中等宽度实线边框。这是因为前景色是默认应用到边框上的。如果你想，你可以用属性 `border-color` 覆盖它:

```css
p.aside {
  color: gray;
  border-style: solid;
  border-color: black;
}
```

This rule will make the text gray, while the borders will be black in color. Any value set for `border-color` will always override the value of `color`.

> 此规则将使文本为灰色，而边框为黑色。为“border-color”设置的任何值都会覆盖“color”的值。

This “borders get the foreground color” behavior is due to the use of a special color keyword, `currentColor`. The value of `currentColor` for any element is the computed value of `color`. So, somewhere inside the user agent’s default styles, there’s a rule that looks something like this:

> 这种“边框获取前景色”的行为是由于使用了一个特殊的颜色关键字“currentColor”。任何元素的' currentColor '的值都是' color '的计算值。因此，在用户代理的默认样式中，有一条规则是这样的:

```css
* {
  border-color: currentColor;
}
```

Thus, if you don’t assign a border a color, that built-in rule will pick up the value of `color` from the element and apply it to any visible borders. If you do assign a border a color, then your color will override the built-in `currentColor` style.

> 此规则将使文本为灰色，而边框为黑色。为“border-color”设置的任何值都会覆盖“color”的值。

Thanks to this, you can also change the foreground color of images. Since images are already composed of colors, you can’t really affect their content using `color`, but you can change the color of any border that appears around the image. This can be done using either `color` or `border-color`. Therefore, the following rules will have the same visual effect on images of class `type1` and `type2`, as shown in Figure 9-4, which is the result of the following code:

> 这种“边框获取前景色”的行为是由于使用了一个特殊的颜色关键字“currentColor”。任何元素的' currentColor '的值都是' color '的计算值。因此，在用户代理的默认样式中，有一条规则是这样的:

```css
img.type1 {
  border-style: solid;
  color: gray;
}
img.type2 {
  border-style: solid;
  border-color: gray;
}
```

<Figures figure="9-4">Setting the border color for images</Figures>

### 9.1.3 Affecting Form Elements

Setting a value for `color` should (in theory, anyway) apply to form elements. Declaring `select` elements to have dark gray text should be as simple as this:

> 为“color”设置一个值应该(至少在理论上)应用于表单元素。声明' select '元素有深灰色文本应该像这样简单:

```css
select {
  color: rgb(33%, 33%, 33%);
}
```

This might also set the color of the borders around the edge of the `select` element, or it might not. It all depends on the user agent and its default styles.

> 这也可能设置“select”元素边缘的颜色，也可能不设置。这完全取决于用户代理及其默认样式。

You can also set the foreground color of input elements—although, as you can see in Figure 9-5, doing so would apply that color to all inputs, from text to radio button to checkbox inputs:

> 您还可以设置输入元素的前景色—尽管，正如您在图 9-5 中所看到的，这样做可以将该颜色应用于所有输入，从文本到单选按钮再到复选框输入:

```css
select {
  color: rgb(33%, 33%, 33%);
}
input {
  color: red;
}
```

<Figures figure="9-5">Changing form element foregrounds</Figures>

Note in Figure 9-5 that the text color next to the checkboxes is still black. This is because the rules shown assign styles only to elements like `input` and `select`, not normal paragraph (or other) text.

> 注意，在图 9-5 中，复选框旁边的文本颜色仍然是黑色的。这是因为显示的规则只将样式分配给“input”和“select”这样的元素，而不是常规的段落(或其他)文本。

Also note that the checkmark in the checkbox is black. This is due to the way form elements are handled in some web browsers, which typically use the form widgets built into the base operating system. Thus, when you see a checkbox and checkmark, they really aren’t content in the HTML document—they’re user interface widgets that have been inserted into the document, much as an image would be. In fact, form inputs are, like images, replaced elements. In theory, CSS does not style the contents of replaced elements.

> 还要注意复选框中的复选标记是黑色的。这是由于在某些 web 浏览器中处理表单元素的方式，这些浏览器通常使用构建到基本操作系统中的表单小部件。因此，当您看到复选框和复选标记时，它们实际上并不是 HTML 文档中的内容—它们是插入到文档中的用户界面小部件，就像图像一样。实际上，表单输入就像图像一样，是被替换的元素。从理论上讲，CSS 不会对被替换元素的内容进行样式化。

In practice, the line is a lot blurrier than that, as Figure 9-5 demonstrates. Some form inputs have the color of their text and even portions of their UI changed, while others do not. And since the rules aren’t explicitly defined, behavior is inconsistent across browsers. In short, form elements are deeply tricky to style and should be approached with extreme caution.

> 实际上，这条线要比这条线模糊得多，如图 9-5 所示。一些表单输入改变了文本的颜色，甚至改变了 UI 的一部分，而另一些则没有。由于没有显式地定义规则，因此不同浏览器之间的行为是不一致的。简而言之，形式元素是非常棘手的风格，应该非常谨慎地处理。

### 9.1.4 Inheriting Color

As the definition of `color` indicates, the property is inherited. This makes sense, since if you declare `p {color: gray;}`, you probably expect that any text within that paragraph will also be gray, even if it’s emphasized or boldfaced or whatever. If you `want` such elements to be different colors, that’s easy enough, as illustrated in Figure 9-6, which is the result of the following code:

> 正如“color”的定义所示，属性是继承的。这是有道理的，因为如果您声明“p {color: gray;}”，您可能会期望该段中的任何文本都是灰色的，即使它被强调或加粗或其他什么。如果你想让这些元素有不同的颜色，这很简单，如图 9-6 所示，这是以下代码的结果:

```css
em {
  color: red;
}
p {
  color: gray;
}
```

<Figures figure="9-6">Different colors for different elements</Figures>

Since color is inherited, it’s theoretically possible to set all of the ordinary text in a document to a color, such as red, by declaring `body {color: red;}`. This should make all text that is not otherwise styled (such as anchors, which have their own color styles) red.

> 由于颜色是继承的，所以理论上可以通过声明“body {color: red;}”将文档中的所有普通文本设置为一种颜色，如红色。这应该使所有没有其他样式的文本(如锚，它们有自己的颜色样式)为红色。

## 9.2 Backgrounds

By default, the background area of an element consists of all of the space behind the foreground out to the outer edge of the borders; thus, the content box and the padding are all part of an element’s background, and the borders are drawn on top of the background. (You can change that to a degree with CSS, as we’ll see shortly.)

> 默认情况下，元素的背景区域由前景后面到边框外边缘的所有空间组成;因此，内容框和填充都是元素背景的一部分，而边框则绘制在背景之上。(您可以使用 CSS 将其改变到一定程度，稍后我们将看到这一点。)

CSS lets you apply a solid color to the background of an element, as well as apply one or more images to the background of a single element, or even describe your own linear and radial gradients.

> CSS 允许您对元素的背景应用纯色，以及对单个元素的背景应用一个或多个图像，甚至可以描述您自己的线性和径向梯度。

### 9.2.1 Background Colors

To declare a color for the background of an element, you use the property `background-color`, which accepts any valid color value.

> 要声明元素的背景颜色，可以使用属性“background-color”，它接受任何有效的颜色值。

<Cards cards="background-color" />

If you want the color to extend out a little bit from the text in the element, add some padding to the mix, as illustrated in Figure 9-7, which is the result of the following code:

> 如果你想让颜色从元素的文本扩展一点，添加一些填充到混合中，如图 9-7 所示，这是以下代码的结果:

```css
p {
  background-color: #aea;
}
p.padded {
  padding: 1em;
}
```

```html
<p>A paragraph.</p>
<p class="padded">A padded paragraph.</p>
```

<Figures figure="9-7">Backgrounds and padding</Figures>

You can set a background color for just about any element, from `body` all the way down to inline elements such as `em` and `a`. The value of `background-color` is not inherited. Its default value is the keyword `transparent`, which makes some sense: if an element doesn’t have a defined color, then its background should be transparent so that the background of its ancestor elements will be visible.

> 您可以为几乎任何元素设置背景颜色，从' body '一直到' em '和' a '等内联元素。“background-color”的值不是继承的。它的默认值是关键字‘transparent’，这是有意义的:如果一个元素没有一个定义的颜色，那么它的背景应该是透明的，这样它的祖先元素的背景就可以看到了。

One way to picture what that means is to imagine a clear (i.e., transparent) plastic sign mounted to a textured wall. The wall is still visible through the sign, but this is not the background of the sign; it’s the background of the wall (in CSS terms, anyway). Similarly, if you set the page canvas to have a background, it can be seen through all of the elements in the document that don’t have their own backgrounds. They don’t inherit the background; it is visible `through` them. This may seem like an irrelevant distinction, but as you’ll see when we discuss background images, it’s a critical difference.

> 一种描绘这意味着什么是想象一个明确的(即。(透明)塑料标牌安装在有纹理的墙壁上。墙上的标志仍然清晰可见，但这不是标志的背景;它是墙壁的背景(反正是 CSS 术语)。类似地，如果将页面画布设置为有背景，则可以通过文档中没有背景的所有元素看到它。他们不继承背景;它是可见的“通过”他们。这似乎是一个无关紧要的区别，但当我们讨论背景图像时，您将看到，这是一个关键的区别。

Most of the time, you’ll have no reason to use the keyword `transparent`, since that’s the default value. On occasion, though, it can be useful. Imagine that a user has set his browser to make all links have a white background. When you design your page, you set anchors to have a white foreground, and you don’t want a background on those anchors. In order to make sure your design choice prevails, you would declare:

> 大多数情况下，你没有理由使用“透明”这个关键字，因为这是默认值。不过，有时它也很有用。假设一个用户将他的浏览器设置为所有链接都是白色背景。当你设计你的页面时，你设置的锚点有一个白色的前景，你不希望这些锚点有背景。为确保你的设计方案获得采纳，你应声明:

```css
a {
  color: white;
  background-color: transparent;
}
```

If you left out the background color, your white foreground would combine with the user’s white background to yield totally unreadable links. This is an unlikely example, but it’s still possible.

> 如果你省略了背景颜色，你的白色前景将与用户的白色背景相结合，产生完全不可读的链接。这是一个不太可能的例子，但仍然是可能的。

The potential combination of author and reader styles is the reason why a CSS validator will generate warnings such as, “You have no `background-color` with your `color`.” It’s trying to remind you that author-user color interaction can occur, and your rule has not taken this possibility into account. Warnings do not mean your styles are invalid: only errors prevent validation.

> 作者和阅读器样式的潜在组合是 CSS 验证器将生成警告的原因，比如“您的‘color’中没有‘background-color’。”它试图提醒你，作者和用户之间可能会发生颜色交互，而你的规则没有考虑到这种可能性。警告并不意味着样式无效:只有错误才能阻止验证。

#### Special effects

By combining `color` and `background-color`, you can create some interesting effects:

> 通过结合“color”和“background-color”，你可以创建一些有趣的效果:

```css
h1 {
  color: white;
  background-color: rgb(20%, 20%, 20%);
  font-family: Arial, sans-serif;
}
```

This example is shown in Figure 9-8.

> 此示例如图 9-8 所示。

<Figures figure="9-8">A reverse-text effect for H1 elements</Figures>

There are as many color combinations as there are colors, and I can’t show all of them here. Still, I’ll try to give you some idea of what you can do.

> 有多少种颜色组合就有多少种颜色，我不能在这里全部展示。尽管如此，我还是会试着告诉你你能做些什么。

This stylesheet is a little more complicated, as illustrated by Figure 9-9, which is the result of the following code:

> 这个样式表稍微复杂一些，如图 9-9 所示，它是以下代码的结果:

```css
body {
  color: black;
  background-color: white;
}
h1,
h2 {
  color: yellow;
  background-color: rgb(0, 51, 0);
}
p {
  color: #555;
}
a:link {
  color: black;
  background-color: silver;
}
a:visited {
  color: gray;
  background-color: white;
}
```

<Figures figure="9-9">The results of a more complicated stylesheet</Figures>

And then there’s the fascinating question of what happens when you apply a background to a replaced element, such as an image. I’m not even talking about images with transparent portions, like a GIF87a or a PNG. Suppose you want to create a twotone border around a JPEG. You can pull that off by adding a background color and a little bit of padding to your image, as illustrated in Figure 9-10, which is the result of the following code:

> 还有一个有趣的问题，当你把一个背景应用到一个被替换的元素上，比如一个图像，会发生什么。我甚至不是在讨论带有透明部分的图像，比如 GIF87a 或 PNG。假设您想在 JPEG 周围创建两个边框。你可以通过添加一个背景颜色和一点填充到你的图像，如图 9-10 所示，这是以下代码的结果:

```css
img.twotone {
  background-color: red;
  padding: 5px;
  border: 5px solid gold;
}
```

<Figures figure="9-10">Using background and border to two-tone an image</Figures>

Technically, the background goes to the outer border edge, but since the border is solid and continuous, we can’t see the background behind it. The one pixel of padding allows a thin ring of background to be seen between the image and its border, creating the visual effect of an “inner border.” This technique could be extended to create more complicated effects with background images like gradients, which we’ll discuss later in the chapter.

> 从技术上讲，背景是外边界的边缘，但是因为边界是连续的，所以我们看不到它后面的背景。一个像素的填充允许在图像和边框之间看到一个薄的背景环，创建一个“内边框”的视觉效果。这种技术可以扩展到创建更复杂的背景图像效果，如渐变，我们将在后面的章节中讨论。

<Tips tips="blue">Note that there are also much more powerful border options available in CSS, so background-and-padding tricks may or may not be useful, depending on what you want to do. See Chapter 8 for details.</Tips>

Remember that form inputs, nearly all of which are replaced elements, are treated as special, and often applying padding to them will not have the same results as applying padding to an image, let alone a nonreplaced element like a paragraph. Just as with most styling of form inputs, adding a background color should be rigorously tested and avoided if possible.

> 请记住，几乎所有的表单输入都是被替换的元素，它们都被视为特殊的，对它们应用填充通常不会得到与对图像应用填充相同的结果，更不用说像段落这样的不可替换元素了。就像大多数表单输入的样式一样，添加背景颜色应该经过严格的测试，如果可能的话应该避免。

### 9.2.2 Clipping the Background

In the previous section, we saw how backgrounds fill out the entire background area of an element. Historically, that extended all the way to the outer edge of the border so that any border with transparent parts (like dashed or dotted borders) would have the background color fill into those transparent parts. Now there’s a CSS property called `background-clip` that lets you affect how far out an element’s background will go.

> 在前一节中，我们了解了背景如何填充元素的整个背景区域。从历史上看，它一直延伸到边界的外边缘，因此任何带有透明部分的边界(如虚线或虚线边界)都将背景颜色填充到这些透明部分中。现在有一个名为“background-clip”的 CSS 属性，它可以让你影响一个元素的背景会走多远。

<Cards cards="background-clip" />

The default value is the historical value: the `background painting area` (which is what `background-clip` defines) extends out to the outer edge of the border. The background will `always` be drawn behind the visible parts of the border, if any.

> 默认值是历史值:“背景绘画区域”(这是“background-clip”定义的)延伸到边界的外边缘。背景将“始终”被绘制在边界的可视部分(如果有的话)后面。

If you choose the value `padding-box`, then the background will only extend to the outer edge of the padding area (which is also the inner edge of the border). Thus, it won’t be drawn behind the border. The value `content-box`, on the other hand, restricts the background to just the content area of the element.

> 如果您选择的值为“padd- box”，那么背景将只会扩展到填充区域的外边缘(也就是边框的内缘)。因此，它不会被画在边界后面。另一方面，值“content-box”将背景限制为元素的内容区域。

The effects of these three values is illustrated in Figure 9-11, which is the result of the following code:

> 这三个值的效果如图 9-11 所示，这是以下代码的结果:

```css
div[id] {
  color: navy;
  background: silver;
  padding: 1em;
  border: 5px dashed;
}
#ex01 {
  background-clip: border-box;
} /* default value */
#ex02 {
  background-clip: padding-box;
}
#ex03 {
  background-clip: content-box;
}
```

<Figures figure="9-11">The three box-oriented types of background clipping</Figures>

That might seem pretty simple, but there are some caveats. The first is that `background-clip` has no effect on the root element (in HTML, that’s either the `html` or `body` element, depending on how your styles are written). This has to do with how the background painting of the root element has to be handled.

> 这可能看起来很简单，但是有一些注意事项。第一个是' background-clip '对根元素没有影响(在 HTML 中，根元素是' HTML '或' body '元素，这取决于您的样式是如何编写的)。这与如何处理根元素的背景绘制有关。

The second is that the exact clipping of the background area can be reduced if the element has rounded corners, thanks to the property `border-radius`. This is basically common sense, since if you give your element significantly rounded corners, you want the background to be clipped by those corners instead of stick out past them. The way to think of this is that the background painting area is determined by `background-clip`, and then any corners that have to be further clipped by rounded corners are appropriately clipped.

> 第二，如果元素有圆角，背景区域的精确裁剪可以减少，这要归功于“border-radius”属性。这基本上是常识，因为如果你给你的元素明显的圆角，你希望背景被这些角剪切而不是突出它们。考虑这个问题的方法是，背景绘画区域是由“background-clip”决定的，然后任何需要被圆角进一步剪切的角落都会被适当地剪切。

The third caveat is that the value of `background-clip` can interact poorly with some of the more interesting values of `background-repeat`, which we’ll get to later on.

> 第三个警告是，“background-clip”的值与“background-repeat”的一些更有趣的值之间的交互效果很差，我们稍后将对此进行讨论。

The fourth is that `background-clip` defines the clipping area of the `background`. It doesn’t affect other background properties. When it comes to flat background colors, that’s a distinction without meaning; but when it comes to background images, which we’ll talk about in the next section, it can make a great deal of difference.

> 第四，“background-clip”定义了“background”的剪切区域。它不会影响其他背景属性。当涉及到平面背景颜色时，这是一个没有意义的区别;但是当涉及到背景图像时，我们将在下一节中讨论，它可以产生很大的差异。

The last value, `text`, clips the background to the text of the element. In other words, the text is “filled in” with the background, and the rest of the element’s background area remains transparent. This is a simple way to add textures to text, by “filling in” the text of an element with its background.

> 最后一个值“text”将背景剪辑为元素的文本。换句话说，文本被背景“填充”，元素的其余背景区域保持透明。这是一种向文本添加纹理的简单方法，方法是用背景“填充”元素的文本。

The kicker is that in order to see this effect, you have to remove the foreground color of the element. Otherwise, the foreground color obscures the background. Consider the following, which has the result shown in Figure 9-12:

> 问题是，为了看到这种效果，您必须删除元素的前景色。否则，前景色会使背景模糊不清。考虑如下，其结果如图 9-12 所示:

```css
div {
  color: rgb(255, 0, 0);
  background: rgb(0, 0, 255);
  padding: 0 1em;
  margin: 1.5em 1em;
  border: 5px dashed;
  font-weight: bold;
}
#ex01 {
  background-clip: text;
  color: transparent;
}
#ex02 {
  background-clip: text;
  color: rgba(255, 0, 0, 0.5);
}
#ex03 {
  background-clip: text;
}
```

<Figures figure="9-12">Clipping the background to the text</Figures>

For the first example, the foreground color is made completely transparent, and the blue background is only visible where it intersects with the text shapes in the element’s content. It is not visible through the image inside the paragraph, since an image’s foreground can’t be set to `transparent`.

> 对于第一个示例，前景颜色是完全透明的，蓝色背景只在与元素内容中的文本形状相交的地方可见。它不能通过段落内的图像看到，因为图像的前景不能设置为“透明”。

In the second example shown in Figure 9-12, the foreground color has been set to `rgba(255,0,0,0.5)`, which is a half-opaque red. The text there is rendered purple, because the half-opaque red combines with the blue underneath. The borders, on the other hand, blend their half-opaque red with the white background behind them, yielding a light red.

> 在图 9-12 所示的第二个示例中，前景色被设置为' rgba(255,0,0,0.5) '，这是一种半不透明的红色。这里的文本呈现紫色，因为半不透明的红色与下面的蓝色相结合。另一方面，边框将半透明的红色与背后的白色背景混合在一起，形成淡红色。

In the third example, the foreground color is a solid, opaque red. The text and borders are both fully red, with no hint of the blue background. It can’t be seen in this instance, because it’s been clipped to the text. The foreground just completely obscures the background.

> 在第三个例子中，前景色是一种固体的、不透明的红色。文本和边框都是完全红色的，没有蓝色背景的提示。在这个例子中看不到它，因为它被剪切到文本中了。前景完全遮住了背景。

This technique works for any background, including gradient and image backgrounds, topics which we’ll cover in a bit. Remember, however: if the background for some reason fails to be drawn behind the text, the transparent text meant to be “filled” with the background will instead be completely unreadable.

> 这种技术适用于任何背景，包括渐变和图像背景，我们稍后将讨论这些主题。但是，请记住:如果由于某种原因不能在文本后面绘制背景，那么原本要用背景“填充”的透明文本将完全不可读。

<Tips tips="orange">As of late 2017, only Firefox supported <code>background-clip: text</code> in that exact form. However, pretty much every browser, <code>including</code> Firefox, supported the variant <code>-webkit-background-clip: text</code>.</Tips>

### 9.2.3 Background Images

Having covered the basics of foreground and background colors, we turn now to the subject of background images. Back in the days of HTML 3.2, it was possible to `associate` an image with the background of the document by using the `BODY` attribute `BACKGROUND`:

> 在介绍了前景和背景颜色的基础知识之后，我们现在开始介绍背景图像。在 HTML 3.2 的时代，可以使用“BODY”属性“background”将图像与文档的背景“关联”起来:

```html
<body background="bg23.gif"></body>
```

This caused a user agent to load the file `bg23.gif` and then “tile” it in the document background, repeating it in both the horizontal and vertical directions to fill up the entire background of the document. This effect can be easily recreated in CSS, but CSS can do a great deal more than simple tiling of background images. We’ll start with the basics and then work our way up.

> 这导致用户代理加载文件“bg23”。然后在文档背景中“平铺”它，在水平和垂直方向重复它来填充整个文档的背景。这种效果可以很容易地在 CSS 中重新创建，但 CSS 可以做的远不止简单地平铺背景图像。我们先从基础开始，然后逐步提高。

#### Using an image

In order to get an image into the background in the first place, use the property `background-image`.

> 为了让一个图像进入背景首先，使用属性' background-image '。

<Cards cards="background-image" />

The default value of `none` means about what you’d expect: no image is placed in the background. If you want a background image, you must give this property at least one other value, like this:

> “none”的默认值表示您所期望的:背景中没有图像。如果你想要一个背景图像，你必须给这个属性至少一个其他的值，像这样:

```css
body {
  background-image: url(bg23.gif);
}
```

Due to the default values of other background properties, this will cause the image bg23.gif to be tiled in the document’s background, as shown in Figure 9-13. As you’ll discover shortly, this isn’t the only option.

> 由于其他背景属性的默认值，这将导致图像 bg23.gif 被平铺在文档的背景中，如图 9-13 所示。您很快就会发现，这并不是惟一的选择。

It’s usually a good idea to specify a background color to go along with your background image; we’ll come back to that concept a little later on. (We’ll also talk about how to have more than one image at the same time, but for now we’re going to stick to just one background image per element.)

> 为你的背景图像指定一个背景颜色通常是一个好主意;我们稍后会回到这个概念。(我们还将讨论如何同时拥有多个图像，但现在我们只对每个元素使用一个背景图像。)

You can apply a background image to any element, block-level or inline:

> 你可以应用背景图像的任何元素，块级或内联:

```css
p.starry {
  background-image: url(http://www.site.web/pix/stars.gif);
  color: white;
}
a.grid {
  background-image: url(smallgrid.gif);
}
```

```html
<p class="starry">
  It's the end of autumn, which means the stars will be brighter than ever!
  <a href="join.html" class="grid">Join us</a> for a fabulous evening of
  planets, stars, nebulae, and more...
</p>
```

<Figures figure="9-13">Applying a background image in CSS</Figures>

As you can see in Figure 9-14, we’ve applied a background to a single paragraph and no other part of the document. We can customize even further, such as placing background images on inline elements like hyperlinks, also depicted in Figure 9-14. If you want to be able to see the tiling pattern, the image will probably need to be pretty small. After all, individual letters aren’t that large!

> 正如您在图 9-14 中所看到的，我们将背景应用于单个段落，而不是文档的其他部分。我们可以进一步定制，例如将背景图像放置在内联元素(如超链接)上，如图 9-14 所示。如果您希望能够看到平铺模式，图像可能需要非常小。毕竟，单个字母并没有那么大!

<Figures figure="9-14">Applying background images to block and inline elements</Figures>

There are a number of ways to employ specific background images. You can place an image in the background of `strong` elements in order to make them stand out more. You can fill in the background of headings with a wavy pattern or with little dots.

> 有许多方法来使用特定的背景图像。你可以把一个图像放在“强”元素的背景中，以使它们更加突出。你可以用波浪图案或小圆点来填充标题的背景。

If you combine simple icons with creative attribute selectors, you can (with use of some properties we’ll get to in just a bit) mark when a link points to a PDF, Word document, email address, or other unusual resource, as shown in Figure 9-15, which is the result of the following code:

> 如果你把简单的图标与创造性的属性选择器,你可以(通过使用一些属性的一点)我们会标记一个链接指向 PDF 时,Word 文档,电子邮件地址,或其他不寻常的资源,如图 15 所示,这是下面的代码的结果:

```css
a[href] {
  padding-left: 1em;
  background-repeat: no-repeat;
}
a[href$=".pdf"] {
  background-image: url(/i/pdf-icon.png);
}
a[href$=".doc"] {
  background-image: url(/i/msword-icon.png);
}
a[href^="mailto:"] {
  background-image: url(/i/email-icon.png);
}
```

<Figures figure="9-15">Adding link icons as background images</Figures>

Just like `background-color`, `background-image` is not inherited—in fact, not a single one of the background properties is inherited. Remember also that when specifying the URL of a background image, it falls under the usual restrictions and caveats for `url()` values: a relative URL should be interpreted with respect to the stylesheet.

> 就像“background-color”一样，“background-image”并没有被继承——事实上，没有一个背景属性被继承。还请记住，在指定背景图像的 URL 时，它受到“URL()”值的常见限制和警告:相对 URL 应该根据样式表进行解释。

#### Why backgrounds aren’t inherited

Earlier, I specifically noted that backgrounds are not inherited. Background images demonstrate why inherited backgrounds would be a bad thing. Imagine a situation where backgrounds were inherited, and you applied a background image to the `body`. That image would be used for the background of every element in the document, with each element doing its own tiling, as shown in Figure 9-16.

> 早些时候，我特别指出，背景不是遗传的。背景图片展示了为什么遗传背景是一件坏事。想象一个场景，背景被继承，你将一个背景图像应用到“body”上。该图像将用于文档中每个元素的背景，每个元素都有自己的平铺，如图 9-16 所示。

<Figures figure="9-16">What inherited backgrounds would do to layout</Figures>

Note how the pattern restarts at the top left of every element, including the links. This isn’t what most authors would want, and this is why background properties are not inherited. If you do want this particular effect for some reason, you can make it happen with a rule like this:

> 注意模式是如何在每个元素(包括链接)的左上角重新启动的。这不是大多数作者想要的，这也是为什么背景属性没有被继承的原因。如果你出于某种原因想要这种效果，你可以使用这样的规则:

```css
* {
  background-image: url(yinyang.png);
}
```

Alternatively, you could use the value inherit like this:

> 或者，您可以像这样使用值 inherit:

```css
body {
  background-image: url(yinyang.png);
}
* {
  background-image: inherit;
}
```

#### Good background practices

Images are laid on top of whatever background color you specify. If you’re completely tiling a JPEG or other opaque image type, this fact doesn’t really make a difference, since a fully tiled image will fill up the document background, leaving nowhere for the color to “peek through,” so to speak. However, image formats with an alpha channel, such as PNG or SVG, can be partially or wholly transparent, which will cause the image to be “combined” with the background color. In addition, if the image fails to load for some reason, then the user agent will use the background color specified in place of the image. Consider how the “starry paragraph” example would look if the background image failed to load, as in Figure 9-17.

> 图像被放置在您指定的任何背景颜色上。如果您正在完全平铺 JPEG 或其他不透明的图像类型，这实际上并没有什么区别，因为一个完全平铺的图像将填满文档背景，没有地方让颜色“偷看”，也就是说。然而，带有 alpha 通道的图像格式，如 PNG 或 SVG，可以是部分或完全透明的，这将导致图像与背景颜色“结合”。此外，如果由于某种原因无法加载图像，则用户代理将使用指定的背景颜色来替代图像。考虑一下，如果背景图像加载失败，“星型段落”示例会是什么样子，如图 9-17 所示。

<Figures figure="9-17">The consequences of a missing background image</Figures>

Figure 9-17 demonstrates why it’s always a good idea to specify a background color when using a background image, so that you’ll at least get a legible result:

> 图 9-17 演示了为什么在使用背景图像时指定背景颜色总是一个好主意，这样至少可以得到一个清晰的结果:

```css
p.starry {
  background-image: url(http://www.site.web/pix/stars.gif);
  background-color: black;
  color: white;
}
a.grid {
  background-image: url(smallgrid.gif);
}
```

```html
<p class="starry">
  It's the end of autumn, which means the stars will be brighter than ever!
  <a href="join.html" class="grid">Join us</a> for a fabulous evening of
  planets, stars, nebulae, and more...
</p>
```

This will fill in a flat-black background if the “starry” image can’t be rendered for some reason. It will also fill in any transparent areas of the background images, or any area of the background that the images don’t cover for some reason. (And there are several reasons they might not, as we’ll soon see.)

> 这将填补一个平面的黑色背景，如果“星光”图像不能被渲染的原因。它还将填充背景图像的任何透明区域，或由于某种原因图像没有覆盖的任何背景区域。(我们很快就会看到，他们可能不会这么做的原因有好几个。)

### 9.2.4 Background Positioning

OK, so we can put images in the background of an element. How about being able to decide exactly how the image is placed? No problem! `background-position` is here to help.

> 我们可以把图像放到元素的背景中。如何能够准确地确定图像的位置呢?没问题!“background-position”可以帮上忙。

<Cards cards="background-position" />

That value syntax looks pretty horrific, but it isn’t; it’s just what happens when you try to formalize the fast-and-loose implementations of a new technology into a regular syntax and then layer even more features on top of that while trying to reuse parts of the old syntax. (So, OK, kind of horrific.) In practice, `background-position` is pretty simple.

> 那个值语法看起来很可怕，但它不是;当你试图将一种新技术的快而松的实现形式化为一种常规语法，然后在此基础上添加更多的特性，同时尝试重用部分旧语法时，就会发生这种情况。(好吧，有点可怕。)实际上，“背景-立场”非常简单。

<Tips tips="blue">Throughout this section, we’ll be using the rule <code>backgroundrepeat: no-repeat</code> to prevent tiling of the background image. You’re not crazy: we haven’t talked about <code>background-repeat</code> yet! We will soon enough, but for now, just accept that the rule restricts the background to a single image, and don’t worry about it until we move on to discussing <code>background-repeat</code>.</Tips>

For example, we can center a background image in the `body` element, with the result depicted in Figure 9-18, which is the result of the following code:

> 例如，我们可以在“body”元素中居中一个背景图像，结果如图 9-18 所示，这是以下代码的结果:

```css
body {
  background-image: url(yinyang.png);
  background-repeat: no-repeat;
  background-position: center;
}
```

<Figures figure="9-18">Centering a single background image</Figures>

We actually placed a single image in the background and then prevented it from being repeated with `background-repeat` (which is discussed in an upcoming section). Every background that includes an image starts with a single image. This starting image is called the origin image.

> 我们实际上在背景中放置了一个单一的图像，然后用“background-repeat”(这将在接下来的章节中讨论)防止它被重复。每个包含图像的背景都是从单个图像开始的。这个起始图像称为原始图像。

The placement of the origin image is accomplished with `background-position`, and there are several ways to supply values for this property. First off, there are the keywords `top`, `bottom`, `left`, `right`, and `center`. Usually, these appear in pairs, but (as the previous example shows) this is not always true. Then there are length values, such as `50px` or `2cm`; and finally, percentage values, such as `43%`. Each type of value has a slightly different effect on the placement of the background image.

> 原始图像的放置是通过“background-position”完成的，有几种方法可以为这个属性提供值。首先，有“顶部”、“底部”、“左侧”、“右侧”和“中间”等关键词。通常，它们成对出现，但是(如前面的示例所示)并不总是这样。然后是长度值，如' 50px '或' 2cm ';最后是百分比值，如“43%”。每种类型的值对背景图像的位置有略微不同的影响。

#### Keywords

The image placement keywords are easiest to understand. They have the effects you’d expect from their names; for example, top right would cause the origin image to be placed in the top-right corner of the element’s background. Let’s go back to the small yin-yang symbol:

> 图像放置关键字最容易理解。他们的名字具有你所期望的效果;例如，右上角将导致原始图像被放置在元素背景的右上角。让我们回到小的阴阳符号:

```css
p {
  background-image: url(yinyang-sm.png);
  background-repeat: no-repeat;
  background-position: top right;
}
```

This will place a nonrepeated origin image in the top-right corner of each paragraph’s background. Incidentally, the result, shown in Figure 9-19, would be exactly the same if the position were declared as `right top`.

> 这将在每个段落的右上角放置一个不重复的原始图像。顺便说一句，如图 9-19 所示，如果位置被声明为“right top”，结果将完全相同。

<Figures figure="9-19">Placing the background image in the top-right corner of paragraphs</Figures>

Position keywords can appear in any order, as long as there are no more than two of them—one for the horizontal and one for the vertical. If you use two horizontal (`right right`) or two vertical (`top top`) keywords, the whole value is ignored.

> 位置关键字可以以任何顺序出现，只要不超过两个位置关键字—一个用于水平位置，一个用于垂直位置。如果使用两个水平(' right right ')或两个垂直(' top top ')关键字，整个值将被忽略。

If only one keyword appears, then the other is assumed to be `center`. So if you want an image to appear in the top center of every paragraph, you need only declare:

> 如果只出现一个关键字，那么另一个关键字将被假定为“center”。因此，如果你想要一个图像出现在每个段落的顶部中心，你只需要声明:

```css
p {
  background-image: url(yinyang-sm.png);
  background-repeat: no-repeat;
  background-position: top;
}
```

#### Percentage values

Percentage values are closely related to the keywords, although they behave in a more sophisticated way. Let’s say that you want to center an origin image within its element by using percentage values. That’s easy enough:

> 百分比值与关键字密切相关，尽管它们的行为更为复杂。假设您希望使用百分比值将原始图像置于其元素的中心。这是很容易:

```css
p {
  background-image: url(chrome.jpg);
  background-repeat: no-repeat;
  background-position: 50% 50%;
}
```

This causes the origin image to be placed such that its center is aligned with the center of its element’s background. In other words, the percentage values apply to both the element and the origin image.

> 这将使原始图像的位置与元素背景的中心对齐。换句话说，百分比值同时适用于元素和原始图像。

In order to understand what that means, let’s examine the process in closer detail. When you center an origin image in an element’s background, the point in the image that can be described as `50% 50%` (the center) is lined up with the point in the background that can be described the same way. If the image is placed at `0% 0%`, its top-left corner is placed in the top-left corner of the element’s background. `100% 100%` causes the bottom-right corner of the origin image to go into the bottom-right corner of the background. Figure 9-20 contains examples of those values, as well as a few others.

> 为了理解这意味着什么，让我们更详细地研究一下这个过程。当你在一个元素的背景中居中一个原始图像时，图像中可以被描述为“50% 50%”的点(中心)与背景中可以被描述为相同方式的点是对齐的。如果图像被放置在' 0% 0% '，它的左上角被放置在元素背景的左上角。' 100% 100% '使原始图像的右下角进入背景的右下角。图 9-20 包含这些值以及其他一些值的示例。

Thus, if you want to place a single origin image a third of the way across the background and two-thirds of the way down, your declaration would be:

> 因此，如果你想在背景三分之一的地方放置一个单一的原点图像，并在三分之二的地方放置，你的声明将是:

```css
p {
  background-image: url(yinyang-sm.png);
  background-repeat: no-repeat;
  background-position: 33% 66%;
}
```

With these rules, the point in the origin image that is one-third across and two-thirds down from the top-left corner of the image will be aligned with the point that is farthest from the top-left corner of the background. Note that the horizontal value `always` comes first with percentage values. If you were to switch the percentages in the preceding example, the image would be placed two-thirds of the way across the background and one-third of the way down.

> 根据这些规则，原始图像中距左上角 1 / 3 宽、向下 2 / 3 的点将与背景左上角最远的点对齐。请注意，水平值“always”与百分数一起排在前面。如果您要切换前面示例中的百分比，则图像将位于背景的三分之二处，位于背景的三分之一处。

<Figures figure="9-20">Various percentage positions</Figures>

If you supply only one percentage value, the single value supplied is taken to be the horizontal value, and the vertical is assumed to be `50%`. For example:

> 如果您只提供一个百分比值，则将所提供的单个值视为水平值，而垂直值假定为“50%”。例如:

```css
p {
  background-image: url(yinyang-sm.png);
  background-repeat: no-repeat;
  background-position: 25%;
}
```

The origin image is placed one-quarter of the way across the paragraph’s background and halfway down it, as depicted in Figure 9-21.

> 原始图像被放置在段落背景的四分之一处，并在中间，如图 9-21 所示。

<Figures figure="9-21">Declaring only one percentage value means the vertical position evaluates to 50%</Figures>

Table 9-1 gives a breakdown of keyword and percentage equivalencies.

> 表 9-1 列出关键字和相当的百分比。

| Keyword(s)   | Equivalent keywords | Equivalent percentages |
| ------------ | ------------------- | ---------------------- |
| center       | center center       | 50% 50%                |
|              |                     | 50%                    |
| right        | center right        | 100% 50%               |
|              | right center        | 100%                   |
| left         | center left         | 0% 50%                 |
|              | left center         | 0%                     |
| top          | top center          | 50% 0%                 |
|              | center top          |                        |
| bottom       | bottom center       | 50% 100%               |
|              | center bottom       |                        |
| top left     | left top            | 0% 0%                  |
| top right    | right top           | 100% 0%                |
| bottom right | right botto         | 100% 100%              |
| bottom left  | left bottom         | 0% 100%                |

In case you were wondering, the default values for `background-position` are `0% 0%`, which is functionally the same as top left. This is why, unless you set different values for the position, background images always start tiling from the top-left corner of the element’s background.

> 如果您想知道，“background-position”的默认值是“0% 0%”，这在功能上与左上角相同。这就是为什么，除非您为位置设置不同的值，否则背景图像总是从元素背景的左上角开始平铺。

#### Length values

Finally, we turn to length values for positioning. When you supply lengths for the position of the origin image, they are interpreted as offsets from the top-left corner of the element’s background. The offset point is the top-left corner of the origin image; thus, if you set the values `20px 30px`, the top-left corner of the origin image will be 20 pixels to the right of, and 30 pixels below, the top-left corner of the element’s background, as shown (along with a few other length examples) in Figure 9-22, which is the result of the following code:

> 最后，我们使用长度值进行定位。当您为原始图像的位置提供长度时，它们被解释为元素背景左上角的偏移量。偏移点为原始图像的左上角;因此,如果你设置值 20 px 30 px,原始图像的左上角将 20 像素的右边,和 30 像素低,元素的左上角的背景,如图所示(连同其他一些长度例子)在图 9-22 中,这是下面的代码的结果:

```css
background-image: url(chrome.jpg);
background-repeat: no-repeat;
background-position: 20px 30px;
```

<Figures figure="9-22">Offsetting the background image using length measures</Figures>

This is quite different than percentage values because the offset is from one top-left corner to another. In other words, the top-left corner of the origin image lines up with the point specified in the `background-position` declaration.

> 这与百分比值有很大的不同，因为偏移量是从左上角到另一个左上角。换句话说，源图像的左上角与“background-position”声明中指定的点对齐。

You can combine length and percentage values to get a “best of both worlds” effect. Let’s say you need to have a background image that is all the way to the right side of the background and 10 pixels down from the top, as illustrated in Figure 9-23. As always, the horizontal value comes first:

> 您可以组合长度和百分比值，以获得“两全其美”的效果。假设您需要一个背景图像，它一直位于背景的右侧，距离顶部向下 10 个像素，如图 9-23 所示。和往常一样，水平值是第一位的:

```css
p {
  background-image: url(yinyang.png);
  background-repeat: no-repeat;
  background-position: 100% 10px;
  border: 1px dotted gray;
}
```

<Figures figure="9-23">Mixing percentages and length values</Figures>

For that matter, you can get the same result as shown in Figure 9-23 by using `right 10px`, since you’re allowed to mix keywords with lengths and percentages. Bear in mind that the syntax enforces axis order when using nonkeyword values; in other words, if you use a length of percentage, then the horizontal value must `always` come first, and the vertical must `always` come second. That means `right 10px` is fine, whereas `10px right` is invalid and will be ignored (because `right` is not a valid vertical keyword).

> 对于这个问题，您可以通过使用“right 10px”得到与图 9-23 相同的结果，因为您可以将关键字与长度和百分比混合在一起。请记住，在使用非关键字值时，语法强制轴顺序;换句话说，如果使用百分比的长度，则水平值必须“总是”在前面，垂直值必须“总是”在后面。这意味着“right 10px”是正确的，而“10px right”是无效的，将被忽略(因为“right”不是一个有效的垂直关键字)。

#### Negative values

If you’re using lengths or percentages, you can use negative values to pull the origin image outside of the element’s background. Consider the example with the very large yin-yang symbol for a background. At one point, we centered it, but what if we only want part of it visible in the top-left corner of the element’s background? No problem, at least in theory.

> 如果使用长度或百分比，可以使用负值将原始图像拉出元素的背景。考虑以非常大的阴阳符号为背景的示例。在某一点上，我们将它居中，但是如果我们只想让它的一部分在元素背景的左上角可见呢?至少在理论上没有问题。

First, assume that the origin image is 300 pixels tall by 300 pixels wide. Then, assume that only the bottom-right third of the image should be visible. You can get the desired effect (shown in Figure 9-24) like this:

> 首先，假设原始图像是 300 像素高，300 像素宽。然后，假设只有图像的右下角三分之一是可见的。你可以得到想要的效果(如图 9-24 所示)，如下图所示:

```css
body {
  background-image: url(yinyang.png);
  background-repeat: no-repeat;
  background-position: -200px -200px;
}
```

<Figures figure="9-24">Using negative length values to position the origin image</Figures>

Or, say you want just the right half of it to be visible and vertically centered within the element’s background area:

> 或者，你想让它的右半部分是可见的，并在元素的背景区域垂直居中:

```css
body {
  background-image: url(yinyang.png);
  background-repeat: no-repeat;
  background-position: -150px 50%;
}
```

Negative percentages are also possible, although they are somewhat interesting to calculate. The origin image and the element are likely to be very different sizes, for one thing, and that can lead to unexpected effects. Consider, for example, the situation created by the following rule and illustrated in Figure 9-25:

> 负的百分比也是可能的，尽管计算起来有些有趣。首先，原始图像和元素的大小可能非常不同，这可能会导致意想不到的效果。例如，考虑以下规则创建的情况，并在图 9-25 中说明:

```css
p {
  background-image: url(pix/yinyang.png);
  background-repeat: no-repeat;
  background-position: -10% -10%;
  width: 500px;
}
```

<Figures figure="9-25">Varying effects of negative percentage values</Figures>

The rule calls for the point outside the origin image defined by `-10% -10%` to be aligned with a similar point for each paragraph. The image is 300 × 300 pixels, so we know its alignment point can be described as 30 pixels above the top of the image, and 30 pixels to the left of its left edge (effectively `-30px` and `-30px`). The paragraph elements are all the same width (`500px`), so the horizontal alignment point is 50 pixels to the left of the left edge of their backgrounds. This means that each origin image’s left edge will be 20 pixels to the left of the left padding edge of the paragraphs. This is because the `-30px` alignment point of the images lines up with the `-50px` point for the paragraphs. The difference between the two is 20 pixels.

> 规则要求原始图像外的点(-10% -10%)与每个段落的相似点对齐。图像是 300×300 像素，所以我们知道它的对齐点可以描述为图像上方 30 像素，左侧 30 像素(有效的‘-30px’和‘-30px’)。段落元素的宽度都是相同的(' 500px ')，因此水平对齐点位于背景左边缘的左侧 50 像素处。这意味着每个原始图像的左边缘距离段落的左边距为 20 像素。这是因为图像的“-30px”对齐点与段落的“-50px”对齐点对齐。两者之差为 20 像素。

The paragraphs are of differing heights, however, so the vertical alignment point changes for each paragraph. If a paragraph’s background area is 300 pixels high, to pick a semi-random example, then the top of the origin image will line up exactly with the top of the element’s background, because both will have vertical alignment points of `-30px`. If a paragraph is 50 pixels tall, then its alignment point would be `-5px` and the top of the origin image will actually be 25 pixels `below` the top of the background. This is why you can see all the tops of the background images in Figure 9-25—the paragraphs are all shorter than the background image.

> 然而，段落的高度不同，因此每个段落的垂直对齐点也不同。如果一个段落的背景区域是 300 像素高，选取一个半随机的例子，那么原始图像的顶部将与元素背景的顶部完全对齐，因为两者的垂直对齐点都是' -30px '。如果一个段落是 50 像素高，那么它的对齐点将是“-5px”，而原始图像的顶部实际上是背景顶部以下 25 像素。这就是为什么你可以在图 9-25 中看到所有的背景图像的顶部-段落都比背景图像短。

#### Changing the offset edges

OK, it’s time for a confession: throughout this whole discussion of background positioning, I’ve been keeping two things from you. I acted as though the value of `background-position` could have no more than two keywords, and that all offsets were always made from the top-left corner of the background area.

> 好了，现在是坦白的时候了:在整个关于背景定位的讨论中，我对你隐瞒了两件事。我的行为就好像‘background-position’的值最多只能包含两个关键字，而且所有的偏移量都是从背景区域的左上角开始计算的。

That was certainly the case throughout most of the history of CSS, but it’s not true any more. In fact, you can have up to four keywords in a very specific pattern to deliver a very specific feature: changing the edges from which offsets are calculated.

> 在 CSS 的大部分历史中确实是这样的，但现在不再是这样了。实际上，您可以在一个非常特定的模式中使用最多四个关键字来交付一个非常特定的特性:更改计算偏移量的边缘。

Let’s start with a simple example: placing the origin image a third of the way across and 30 pixels down from the top-left corner. Using what we saw in previous sections, that would be:

> 让我们从一个简单的示例开始:将原始图像放置在距离左上角向下 30 个像素的地方，中间距离为三分之一。利用我们在前几节中看到的，这将是:

```css
background-position: 33% 30px;
```

Now let’s do the same thing with this four-part syntax:

> 现在让我们用这四部分的语法做同样的事情:

```css
background-position: left 33% top 30px;
```

What this four-part value says is “from the `left` edge, have a horizontal offset of `33%`; from the `top` edge, have an offset of `30px`.”

> 这个由四部分组成的值表示的是“从‘左侧’边缘开始，水平偏移量为‘33%’;从“顶部”边缘开始，偏移量为“30px”。

Great, so that’s a more verbose way of getting the default behavior. Now let’s change things so the origin image is placed a third of the way across and 30 pixels up from the bottom-right corner, as shown in Figure 9-26 (which assumes no repeating of the background image, for clarity’s sake):

> 很好，这是获得默认行为的一种更详细的方式。现在让我们改变一下，让原始图像放置在距离右下角三分之一处，距离右下角 30 个像素处，如图 9-26 所示(为了清晰起见，假设背景图像没有重复):

```css
background-position: right 33% bottom 30px;
```

<Figures figure="9-26">Changing the oset edges for the origin image</Figures>

Here, we have a value that means “from the `right` edge, have a horizontal offset of `33%`; from the `bottom` edge, have an offset of `30px`.”

> 在这里，我们有一个值，意思是“从‘右’边开始，水平偏移量为‘33%’;从“底部”边缘开始，偏移量为“30px”。

Thus, the general pattern is edge keyword, offset distance, edge keyword, offset distance. You can mix the order of horizontal and vertical information; that is, `bottom 30px right 25%` works just as well as `right 25% bottom 30px`. However, you cannot omit either of the edge keywords; `30px right 25%` is invalid and will be ignored.

> 因此，一般的模式是 edge 关键字、偏移距离、edge 关键字、偏移距离。你可以混合水平和垂直信息的顺序;也就是说，“右下角 30px + 25%”和“右下角 30px + 25%”效果一样。但是，您不能忽略任何一个边缘关键字;“30px 右 25%”无效，将被忽略。

You can omit an offset distance in cases where you want it to be zero. So `right bottom 30px` would put the origin image against the right edge and 30 pixels up from the bottom of the background area, whereas `right 25% bottom` would place the origin image a quarter of the way across from the right edge and up against the bottom.

> 如果您希望偏移距离为零，可以忽略它。因此，“右底部 30px”会将原始图像置于右边缘，而“右底部 25%”则会将原始图像置于右边缘的四分之一处，并向上置于底部。

These are both illustrated in Figure 9-27.

> 这些都在图 9-27 中进行了说明。

<Figures figure="9-27">Inferred zero-length offsets</Figures>

As it happens, you can only define the edges of an element as offset bases, not the center. A value like `center 25% center 25px` will be ignored.

> 实际上，您只能将元素的边定义为偏移基，而不是中心。像' center 25% center 25px '这样的值将被忽略。

### 9.2.5 Changing the Positioning Box

OK, so now we can add an image to the background, and we can even change where the origin image is placed. But what if we don’t want to have its placement calculated with respect to the outer padding edge of the element, which is the default? We can affect that using the property `background-origin`.

> 现在我们可以添加一个图像到背景中，我们甚至可以改变原始图像的位置。但是，如果我们不希望根据元素的外边距(默认值)计算它的位置，该怎么办呢?我们可以使用属性' background-origin '来影响它。

<Cards cards="background-origin" />

This property probably looks very similar to `background-clip`, and with good reason, but its effect is pretty distinct. With `background-origin`, you can determine the edge that’s used to determine placement of the origin image. This is also known as defining the background positioning area. (`background-clip`, you may recall, defined the background painting area.)

> 这个属性可能看起来非常类似于“background-clip”，这是有原因的，但是它的效果非常不同。使用“background-origin”，您可以确定用于确定原始图像位置的边缘。这也被称为定义背景定位区域。(你可能还记得，‘background-clip’定义了背景绘画区域。)

The default, `padding-box`, means that (absent any other changes) the top-left corner of the origin image will be placed in the top-left corner of the outer edge of the padding, which is just inside the border.

> 默认的“拍子框”意味着(没有任何其他变化)原始图像的左上角将被放置在内边框内的内边距外边缘的左上角。

If you use the value `border-box`, then the top-left corner of the origin image will go into the top-left corner of the padding area. That does mean that the border, if any, will be drawn over the origin image (assuming the background painting area wasn’t restricted to be `padding-box` or `content-box`, that is).

> 如果您使用值“border-box”，那么原始图像的左上角将进入填充区域的左上角。这意味着边界(如果有的话)将被绘制在原始图像上(假设背景绘制区域没有被限制为“padd- box”或“content-box”)。

With `content-box`, you shift the origin image to be placed in the top-left corner of the content area. The three different results are illustrated in Figure 9-28:

> 使用“content-box”，您可以将原始图像移动到内容区域的左上角。三种不同的结果如图 9-28 所示:

```css
div[id] {
  color: navy;
  background: silver;
  background-image: url(yinyang.png);
  background-repeat: no-repeat;
  padding: 1em;
  border: 5px dashed;
}
#ex01 {
  background-origin: border-box;
}
#ex02 {
  background-origin: padding-box;
} /* default value */
#ex03 {
  background-origin: content-box;
}
```

<Figures figure="9-28">The three types of background origins</Figures>

Remember that this “placed in the top left” behavior is the default behavior, one you can change with `background-position`. If the origin image is placed somewhere other than the top-left corner, its position will be calculated with respect to the box defined by `background-origin`: the border edge, the padding edge, or the content edge. Consider, for example, this variant on our previous example, which is illustrated in Figure 9-29:

> 请记住，这种“放置在左上角”的行为是默认的行为，您可以使用“background-position”来更改它。如果原始图像放置在左上角以外的地方，它的位置将根据“background-origin”定义的框来计算:边界边缘、填充边缘或内容边缘。例如，考虑我们前面的例子的这种变体，如图 9-29 所示:

```css
div[id] {
  color: navy;
  background: silver;
  background-image: url(yinyang);
  background-repeat: no-repeat;
  background-position: bottom right;
  padding: 1em;
  border: 5px dotted;
}
#ex01 {
  background-origin: border-box;
}
#ex02 {
  background-origin: padding-box;
} /* default value */
#ex03 {
  background-origin: content-box;
}
```

<Figures figure="9-29">The three types of background origins, redux</Figures>

Where things can get `really` interesting is if you’ve explicitly defined your background origin and clipping to be different boxes. Imagine you have the origin placed with respect to the padding edge but the background clipped to the content area, or vice versa. This would have the results shown in Figure 9-30, as resulting from the following:

> 如果你明确定义了背景原点和裁剪为不同的方框，事情就会变得“真正”有趣。想象一下，你把原点放在与填充边相对的位置，但是背景被剪切到内容区域，反之亦然。结果如图 9-30 所示，结果如下:

```css
#ex01 {
  background-origin: padding-box;
  background-clip: content-box;
}
#ex02 {
  background-origin: content-box;
  background-clip: padding-box;
}
```

<Figures figure="9-30">When origin and clipping diverge</Figures>

In the first example shown in Figure 9-29, the edges of the origin image are clipped because it’s been positioned with respect to the padding box, but the background painting area has been clipped at the edge of the content box. In the second example, the origin image is placed with respect to the content box, but the painting area extends into the padding box. Thus, the origin image is visible all the way down to the bottom padding edge, even though its top is not placed against the top padding edge.

> 在图 9-29 所示的第一个示例中，原始图像的边缘被剪切，因为它的位置相对于填充框，但是背景绘画区域被剪切到内容框的边缘。在第二个示例中，原始图像相对于内容框放置，但是绘画区域扩展到填充框。因此，即使原始图像的顶部没有与顶部的填充边缘相冲突，它也可以一直显示到底部的填充边缘。

### 9.2.6 Background Repeating (or Lack Thereof)

In the old days, if you wanted some kind of “sidebar” background effect, you had to create a very short, but incredibly wide, image to place in the background. At one time, a favorite size for these images was 10 pixels tall by 1,500 pixels wide. Most of that image would be blank space; only the left 100 or so pixels contain the “sidebar” image. The rest of the image was basically wasted.

> 在过去，如果你想要一些“边栏”背景效果，你必须创建一个非常短，但难以置信的宽度，图像放在背景中。曾经，这些图片的最佳尺寸是 10 像素高，1500 像素宽。大部分图像都是空白的;只有左边大约 100 个像素包含“边栏”图像。图像的其余部分基本上都被浪费了。

Wouldn’t it be much more efficient to create a sidebar image that’s 10 pixels tall and 100 pixels wide, with no wasted blank space, and then repeat it only in the vertical direction? This would certainly make your design job a little easier, and your users’ download times a lot faster. Enter `background-repeat`.

> 创建一个 10 像素高、100 像素宽、没有浪费空白空间的边栏图像，然后只在垂直方向重复，这样不是更有效吗?这当然会使您的设计工作更容易一些，而且您的用户的下载时间也会快得多。输入“平铺方式”。

<Cards cards="background-repeat" />

The value syntax for `background-repeat` looks a bit complicated at first glance, but it’s really fairly straightforward. In fact, at its base, it’s just four values: `repeat`, `no-repeat`, `space`, and `round`. The other two, `repeat-x` and `repeat-y`, are considered to be shorthand for combinations of the others. Table 9-2 shows how they break down.

> “background-repeat”的值语法乍一看有点复杂，但实际上相当简单。实际上，它的基础只有四个值:“repeat”、“no-repeat”、“space”和“round”。另外两个单词“repeat-x”和“repeat-y”被认为是其他两个单词组合的简写。表 9-2 显示了它们是如何分解的。

If two values are given, the first applies in the horizontal direction, and the second in the vertical. If there is just one value, it applies in both the horizontal and vertical directions, with the exception, as shown in Table 9-2, of `repeat-x` and `repeat-y`.

> 如果给定两个值，则第一个值应用于水平方向，第二个值应用于垂直方向。如果只有一个值，那么它在水平和垂直方向上都适用，除了如表 9-2 所示的“重复-x”和“重复-y”之外。

| Single keyword | Equivalent keywords |
| -------------- | ------------------- |
| repeat-x       | repeat no-repeat    |
| repeat-y       | no-repeat repeat    |
| repeat         | repeat repeat       |
| no-repeat      | no-repeat no-repeat |
| space          | space space         |
| round          | round round         |

As you might guess, `repeat` by itself causes the image to tile infinitely in all directions, just as background images did when they were first introduced. `repeat-x` and `repeat-y` cause the image to be repeated in the horizontal or vertical directions, respectively, and `no-repeat` prevents the image from tiling along a given axis.

> 正如你可能猜到的，“重复”本身会导致图像向各个方向无限平铺，就像背景图像第一次被引入时所做的那样。“重复-x”和“重复-y”分别导致图像在水平或垂直方向上重复，而“不重复”则防止图像沿给定轴平铺。

By default, the background image will start from the top-left corner of an element. Therefore, the following rules will have the effect shown in Figure 9-31:

> 默认情况下，背景图像将从元素的左上角开始。因此，以下规则的效果如图 9-31 所示:

```css
body {
  background-image: url(yinyang-sm.png);
  background-repeat: repeat-y;
}
```

<Figures figure="9-31">Tiling the background image vertically</Figures>

Let’s assume, though, that you want the image to repeat across the top of the document. Rather than creating a special image with a whole lot of blank space underneath, you can just make a small change to that last rule:

> 不过，我们假设您希望图像在文档的顶部重复。而不是创建一个特殊的图像与整个空白空间下方，你可以只做一个小的改变，这最后的规则:

```css
body {
  background-image: url(yinyang-sm.png);
  background-repeat: repeat-x;
}
```

As Figure 9-32 shows, the image is repeated along the `x` axis (that is, horizontally) from its starting position—in this case, the top-left corner of the `body` element’s background area.

> 如图 9-32 所示，图像从起始位置开始沿着“x”轴(即水平方向)重复—在本例中，是“body”元素的背景区域的左上角。

<Figures figure="9-32">Tiling the background image horizontally</Figures>

Finally, you may not want to repeat the background image at all. In this case, you use the value `no-repeat`:

> 最后，您可能根本不想重复背景图像。在这种情况下，你使用值“no-repeat”:

```css
body {
  background-image: url(yinyang-sm.png);
  background-repeat: no-repeat;
}
```

This value may not seem terribly useful, given that the above declaration would just drop a small image into the top-left corner of the document, but let’s try it again with a much bigger symbol, as shown in Figure 9-33, which is the result of the following code:

> 这个值可能不是特别有用，因为上面的声明只是将一个小图像放到文档的左上角，但是让我们用一个更大的符号再试一次，如图 9-33 所示，这是以下代码的结果:

```css
body {
  background-image: url(yinyang.png);
  background-repeat: no-repeat;
}
```

<Figures figure="9-33">Placing a single large background image</Figures>

The ability to control the repeat direction dramatically expands the range of possible effects. For example, let’s say you want a triple border on the left side of each `h1` element in your document. You can take that concept further and decide to set a wavy border along the top of each `h2` element. The image is colored in such a way that it blends with the background color and produces the wavy effect shown in Figure 9-34, which is the result of the following code:

> 控制重复方向的能力极大地扩展了可能的影响范围。例如，假设您希望在文档中每个“h1”元素的左侧有一个三重边框。您可以进一步采取这一概念，并决定设置一个波浪边界沿每个' h2 '元素的顶部。图像的颜色与背景颜色混合，产生如图 9-34 所示的波浪效果，这是以下代码的结果:

```css
h1 {
  background-image: url(triplebor.gif);
  background-repeat: repeat-y;
}
h2 {
  background-image: url(wavybord.gif);
  background-repeat: repeat-x;
  background-color: #ccc;
}
```

<Figures figure="9-34">Bordering elements with background images</Figures>

<Tips tips="green">There are better ways to create a wavy-border effect these daysnotably, the border image properties explored in the section “Image Borders” found in Chapter 8, “Padding, Borders, Outlines, and Margins.”</Tips>

#### Repeating and positioning

In the previous section, we explored the values `repeat-x`, `repeat-y`, and `repeat`, and how they affect the tiling of background images. In each case, the tiling pattern always started from the top-left corner of the element’s background. That’s because, as we’ve seen, the default values for `background-position` are `0% 0%`. Given that you know how to change the position of the origin image, you need to know out how user agents will handle it.

> 在前一节中，我们研究了值' repeat-x '、' repeat-y '和' repeat '，以及它们如何影响背景图像的平铺。在每种情况下，平铺模式总是从元素背景的左上角开始。这是因为，正如我们所看到的，“background-position”的默认值是“0% 0%”。既然您知道如何更改原始图像的位置，您就需要知道用户代理将如何处理它。

It will be easier to show an example and then explain it. Consider the following markup, which is illustrated in Figure 9-35:

> 展示一个例子然后解释它会更容易。考虑下面的标记，如图 9-35 所示:

```css
p {
  background-image: url(yinyang-sm.png);
  background-position: center;
  border: 1px dotted gray;
}
p.c1 {
  background-repeat: repeat-y;
}
p.c2 {
  background-repeat: repeat-x;
}
```

<Figures figure="9-35">Centering the origin image and repeating it</Figures>

So there you have it: stripes running through the center of the elements. It may look wrong, but it isn’t.

> 这样你就有了:条纹贯穿元素的中心。它可能看起来是错的，但它不是。

The examples shown in Figure 9-35 are correct because the origin image has been placed in the center of the first `p` element and then tiled along the `y axis in both directions`—in other words, both up and down. For the second paragraph, the images are repeated to the right `and` left.

> 图 9-35 所示的示例是正确的，因为原始图像被放置在第一个“p”元素的中心，然后沿着“y 轴两个方向”平铺——换句话说，向上和向下。在第二段中，图像在右边和左边重复出现。

Setting an image in the center of the `p` and then letting it fully repeat will cause it to tile in all four directions: up, down, left, and right. The only difference `background-position` makes is in where the tiling starts. Figure 9-36 shows the difference between tiling from the center of an element and from its top-left corner.

> 在“p”的中心设置一个图像，然后让它完全重复，会导致它在所有四个方向平铺:上、下、左、右。“背景位置”的唯一区别在于贴瓷砖的起始位置。图 9-36 显示了从元素中心到左上角的平铺的区别。

<Figures figure="9-36">The difference between centering a repeat and starting it from the top lef</Figures>

Note the differences along the edges of the element. When the background image repeats from the center, as in the first paragraph, the grid of yin-yang symbols is centered within the element, resulting in consistent clipping along the edges. In the second paragraph, the tiling begins at the top-left corner of the padding area, so the clipping is not consistent.

> 请注意元素边缘的差异。当背景图像从中心重复时，如第一段，阴阳符号的网格在元素中居中，导致沿着边缘的一致裁剪。在第二段中，平铺从填充区域的左上角开始，因此剪裁不一致。

<Tips tips="blue">In case you’re wondering, there are no single-direction values such as <code>repeat-left</code> or <code>repeat-up</code>.</Tips>

#### Spacing and rounding

Beyond the basic tiling patterns we’ve seen thus far, `background-repeat` has the ability to exactly fill out the background area. Consider, for example, what happens if we use the value `space` to define the tiling pattern, as shown in Figure 9-37:

> 除了我们目前看到的基本平铺模式之外，“background-repeat”还能够准确地填充背景区域。例如，考虑一下，如果我们使用值' space '来定义平铺模式会发生什么，如图 9-37 所示:

```css
div#example {
  background-image: url(yinyang.png);
  background-repeat: space;
}
```

<Figures figure="9-37">Tiling the background image with filler space</Figures>

If you look closely, you’ll notice that there are background images in each of the four corners of the element. Furthermore, the images are spaced out so that they occur at regular intervals in both the horizontal and vertical directions.

> 如果你仔细观察，你会发现元素的四个角落都有背景图像。此外，这些图像是间隔的，使它们在水平和垂直方向上都有规律地出现。

This is what `space` does: it determines how many repetitions it can fully fit along a given axis, and then spaces them out at regular intervals so that the repetitions go from one edge of the background to another. This doesn’t guarantee a regular square grid, where the intervals are all the same both horizontally and vertically. It just means that you’ll have what look like columns and rows of background images, with likely different horizontal and vertical separations. You can see some examples of this in Figure 9-38.

> 这就是“空间”的作用:它决定了它能在给定的轴上重复多少次，然后按一定的间隔将它们间隔开，这样重复的部分就能从背景的一边到另一边。这并不能保证一个规则的正方形网格，其中水平和垂直的间隔都是相同的。它只是意味着你会有看起来像列和行的背景图像，可能有不同的水平和垂直的分隔。您可以在图 9-38 中看到一些这样的例子。

<Figures figure="9-38">Spaced-out tiling with different intervals</Figures>

<Tips tips="blue">Keep in mind that any background color, or the “backdrop” of the element (that is, the combined background of the element’s ancestors) will show through the gaps in <code>space-separated</code> background images.</Tips>

What happens if you have a really big image that won’t fit more than once along the given axis? Then it’s only drawn once, and placed as determined by the value of `background-position`. The flip side of that is that if more than one repetition of the image will fit along an axis, then the value of `background-position` is ignored along that axis. An example of this is shown in Figure 9-39, and created using the following code:

> 如果你有一个非常大的图像，但在给定的轴上只能放一次，会发生什么?然后它只绘制一次，并由' background-position '的值决定。另一方面，如果一个轴上有多个图像重复，那么“background-position”的值就会被忽略。图 9-39 显示了一个这样的例子，并使用以下代码创建:

```css
div#example {
  background-image: url(yinyang.png);
  background-position: center;
  background-repeat: space;
}
```

<Figures figure="9-39">Spacing along one axis but not the other</Figures>

Notice that the images are spaced horizontally, and thus override the `center` position along that axis, but are not spaced (because there isn’t enough room to do so) and are still centered vertically. That’s the effect of `space` overriding `center` along one axis, but not the other.

> 请注意，图像是水平间隔的，因此覆盖了沿轴的“中心”位置，但没有间隔(因为没有足够的空间这样做)，仍然是垂直居中。这是“空间”在一个轴上压倒“中心”的结果，而不是在另一个轴上。

By contrast, the value `round` will most likely result in some scaling of the background image as it is repeated, `and` (strangely enough) it will not override `background-position`. If an image won’t quite repeat so that it goes from edge to edge of the background, then it will be scaled up `or` down in order to make it fit a whole number of times.

> 相比之下，“round”值很可能会导致背景图像在重复时发生缩放，而且“(奇怪的是)它不会覆盖“background-position”。如果一个图像不会重复，所以它会从边缘到背景的边缘，然后它会被放大或缩小，以使它适应所有的次数。

Furthermore, the images can be scaled differently along each axis, making it the only background property that will automatically alter an image’s intrinsic aspect ratio. (`background-size` can also change the aspect ratio, but only by explicit direction from the author.) You can see an example of this in Figure 9-40, which is the result of the following code:

> 此外，图像可以按不同的比例沿每个轴，使它成为唯一的背景属性，将自动改变图像的固有纵横比。(“background-size”也可以改变长宽比，但只能通过作者明确的指示来实现。)你可以在图 9-40 中看到一个例子，这是以下代码的结果:

```css
body {
  background-image: url(yinyang.png);
  background-position: top left;
  background-repeat: round;
}
```

Note that if you have a background 850 pixels wide and a horizontally rounded image that’s 300 pixels wide, then a browser can decide to use three images and scale them down to fit three-across into the 850 pixel area. (Thus making each instance of the image 283.333 pixels wide.) With `space`, it would have to use two images and put 250 pixels of space between them, but `round` is not so constrained.

> 请注意，如果您有一个 850 像素宽的背景和一个 300 像素宽的水平圆形图像，那么浏览器可以决定使用三个图像，并将它们缩小到 850 像素的区域，以适应三个图像。(从而使图像的每个实例的宽度为 283.333 像素。)如果使用“space”，它将不得不使用两张图片，并在它们之间放置 250 像素的空间，但“round”则没有那么多限制。

<Figures figure="9-40">Tiling the background image with scaling</Figures>

Here’s the interesting wrinkle: while `round` will resize the background images so that you can fit a whole number of them into the background, it will `not` move them to make sure that they actually touch the edges of the background. In other words, the only way to make sure your repeating pattern fits and no background images are clipped is to put the origin image in a corner. If the origin image is anywhere `else`, clipping will occur, as illustrated in Figure 9-41, which is the result of the following code:

> 这里有一个有趣的小窍门:虽然“圆形”会调整背景图片的大小，这样你就可以把大量的图片放入背景中，但它不会移动它们来确保它们确实接触到了背景的边缘。换句话说，确保重复模式合适且不剪切背景图像的唯一方法是将原始图像放在角落中。如果原始图像位于“其他”位置，则会发生裁剪，如图 9-41 所示，这是以下代码的结果:

```css
body {
  background-image: url(yinyang.png);
  background-position: center;
  background-repeat: round;
}
```

<Figures figure="9-41">Rounded background images that are clipped</Figures>

The images are still scaled so that they would fit into the background positioning area a whole number of times. They just aren’t repositioned to actually do so. Thus, if you’re going to use `round` and you don’t want to have any clipped background tiles, make sure you’re starting from one of the four corners (and make sure the background positioning and painting areas are the same; see the section “Tiling and clipping” on page 427 for more).

> 图像仍然是按比例缩放的，以便它们能够多次适合背景定位区域。他们只是没有重新定位，实际上这样做。因此，如果你要使用“圆形”，你不想有任何剪切的背景瓷砖，确保你从四个角中的一个开始(并确保背景位置和绘画区域是相同的;详情请参阅 427 页“平铺和裁剪”一节)。

On the other hand, you can get some interesting effects from the actual behavior of `round`. Suppose you have two elements that are the same size with the same rounded backgrounds, and you place them right next to each other. The background tiling should appear to be one continuous pattern.

> 另一方面，你可以从“回合”的实际行为中得到一些有趣的效果。假设您有两个具有相同大小和相同圆角背景的元素，将它们放在一起。背景平铺应该是一个连续的图案。

#### Tiling and clipping

If you recall, `background-clip` can alter the area in which the background is drawn, and `background-origin` determines the placement of the origin image. So what happens when you’ve made the clipping area and the origin area different, `and` you’re using either `space` or `round` for the tiling pattern?

> 如果你还记得，“background-clip”可以改变绘制背景的区域，而“background-origin”决定了原始图像的位置。那么，当你让裁剪区域和原始区域不同时，会发生什么呢?你会使用“space”还是“round”作为平铺模式?

The basic answer is that if your values for `background-origin` and `background-clip` aren’t the same, you’ll see some clipping. This is because `space` and `round` are calculated with respect to the background positioning area, not the painting area. Some examples of what can happen are shown in Figure 9-42.

> 基本的答案是，如果“background-origin”和“background-clip”的值不相同，您将看到一些剪切。这是因为“空间”和“圆”是根据背景定位区域来计算的，而不是绘画区域。图 9-42 显示了一些可能发生的情况。

<Figures figure="9-42">Clipping due to mismatched clip and origin values</Figures>

This has always been the case, actually, thanks to the historical behavior of CSS, which positioned elements with respect to the inner border edge but clipped them at the outer border edge. Thus, even if you very carefully controlled the size of an element so that it would have an even number of background-image tiles, adding a border would introduce the possibility of partial clipping of tiles. (Especially if a border side color ever got set to `transparent`.)

> 实际上，由于 CSS 的历史行为，这种情况一直都是这样的，它将元素定位在相对于内部边界边缘的位置，而将它们裁剪到外部边界边缘。因此，即使您非常小心地控制元素的大小，使其具有偶数个背景图像块，添加边框也会引入对块进行部分剪切的可能性。(特别是当边框颜色被设置为‘透明’的时候。)

As for the best value to use, that’s a matter of opinion and circumstance. It’s likely that in most cases, setting both `background-origin` and `background-clip` to `padding-box` will get you the results you desire. If you plan to have borders with see-through bits, though, then `border-box` might be a better choice.

> 至于使用的最佳价值，那是意见和环境的问题。在大多数情况下，将“background-origin”和“background-clip”设置为“padding-box”可能会得到您想要的结果。不过，如果你打算用透明的小块来做边框，那么“边框盒”可能是更好的选择。

### 9.2.7 Getting Attached

So, now you can place the origin image for the background anywhere in the background of an element, and you can control (to a large degree) how it tiles. As you may have realized already, placing an image in the center of the `body` element could mean, given a sufficiently long document, that the background image won’t be initially visible to the reader. After all, a browser provides only a window onto the document. If the document is too long to be displayed in the window, then the user can scroll back and forth through the document. The center of the body could be two or three “screens” below the beginning of the document, or just far enough down to push most of the origin image beyond the bottom of the browser window.

> 因此，现在您可以将背景的原始图像放置在元素背景中的任何位置，并且可以(在很大程度上)控制它如何平铺。正如您可能已经意识到的，将一个图像放在“body”元素的中心可能意味着，给定一个足够长的文档，背景图像一开始对读者是不可见的。毕竟，浏览器只提供到文档的窗口。如果文档太长，无法在窗口中显示，那么用户可以在文档中来回滚动。正文的中心可以是文档开头下面的两三个“屏幕”，或者向下足够远，将原始图像的大部分推到浏览器窗口的底部。

Furthermore, even if you assume that the origin image is initially visible, it always scrolls with the document—it’ll vanish every time a user scrolls beyond the location of the image. Never fear: there is a way to prevent this scrolling.

> 而且，即使您假设原始图像最初是可见的，它也总是与文档一起滚动—每当用户滚动超出图像位置时，它就会消失。不要担心:有一种方法可以防止滚动。

<Cards cards="background-attachment" />

Using the property `background-attachment`, you can declare the origin image to be fixed with respect to the viewing area and therefore immune to the effects of scrolling:

```css
body {
  background-image: url(yinyang.png);
  background-repeat: no-repeat;
  background-position: center;
  background-attachment: fixed;
}
```

Doing this has two immediate effects, as you can see in Figure 9-43. The first is that the origin image does not scroll along with the document. The second is that the placement of the origin image is determined by the size of the viewport, not the size (or placement within the viewport) of the element that contains it.

> 这样做有两个直接的效果，如图 9-43 所示。首先，原始图像不会随文档一起滚动。第二，原始图像的位置是由视口的大小决定的，而不是包含它的元素的大小(或视口内的位置)。

<Figures figure="9-43">Nailing the background in place</Figures>

In a web browser, the viewing area can change as the user resizes the browser’s window. This will cause the background’s origin image to shift position as the window changes size. Figure 9-44 depicts another view of the same document, where it’s been scrolled partway through the text.

> 在 web 浏览器中，查看区域可以随着用户调整浏览器窗口的大小而更改。这将导致背景的原始图像随着窗口大小的改变而改变位置。图 9-44 描绘了同一文档的另一个视图，它在文本中被滚动了一半。

Almost the inverse of `fixed` is `local`, which has background images scrolling with content. In this case, though, the effect is only seen when an element’s content has to be scrolled. This is tricky to grasp at first.

> 与“fixed”几乎相反的是“local”，它的背景图像会随着内容滚动。但是，在这种情况下，只有在必须滚动元素的内容时才能看到这种效果。这一点一开始很难理解。

<Figures figure="9-44">The centering continues to hold</Figures>

Consider the following, where no `background-attachment` has been set:

> 考虑一下没有设置 `background-attachment` 的情况:

```css
aside {
  background-image: url(yinyang.png);
  background-position: top right;
  max-height: 20em;
  overflow: scroll;
}
```

In this situation, if the content of an `aside` is taller than 20 em, the rest of the content can be accessed by using a scrollbar. The background image, however, will `not` scroll with the content. It will instead stay in the top-left corner of the element box.

> 在这种情况下，如果“aside”的内容大于 20em，则可以使用滚动条访问其余内容。然而，背景图像不会随内容一起“滚动”。它将停留在元素框的左上角。

By adding `background-attachment: local`, the image is attached ot the local context. The visual effect is rather like an `iframe`, if you have any experience with those. Figure 9-45 shows the results of the previous code sample and the following code side by side:

> 通过添加“background-attachment: local”，图像被附加到本地上下文。视觉效果就像一个“iframe”，如果你有任何经验的话。图 9-45 显示了之前代码示例的结果和下面并排显示的代码:

```css
aside {
  background-image: url(yinyang.png);
  background-position: top right;
  background-attachment: local; /* attaches to content */
  max-height: 20em;
  overflow: scroll;
}
```

<Figures figure="9-45">Default-attach versus local-attach</Figures>

There is one other value for `background-attachment`, and that’s the default value `scroll`. As you might expect, this causes the background image to scroll along with the rest of the document when viewed in a web browser, and it doesn’t necessarily change the position of the origin image as the window is resized. If the document width is fixed (perhaps by assigning an explicit `width` to the `body` element), then resizing the viewing area won’t affect the placement of a scroll-attachment origin image at all.

> “background-attachment”还有另外一个值，那就是默认值“scroll”。正如您所期望的那样，这将导致在 web 浏览器中查看时背景图像与文档的其他部分一起滚动，并且在窗口调整大小时不一定会更改原始图像的位置。如果文档宽度是固定的(可能通过为“body”元素分配一个显式的“宽度”)，那么调整查看区域的大小根本不会影响滚动附件原始图像的位置。

#### Interesting effects

In technical terms, when a background image has been fixed, it is positioned with respect to the viewing area, not the element that contains it. However, the background will be visible only within its containing element. This leads to a rather interesting consequence.

> 在技术术语中，当背景图像被固定时，它的位置是相对于观看区域的，而不是包含它的元素。但是，背景只能在其包含的元素中可见。这导致了一个相当有趣的结果。

Let’s say you have a document with a tiled background that actually looks like it’s tiled, and both `h1` and `h2` elements with the same pattern, only in a different color. Both the `body` and heading elements are set to have fixed backgrounds, resulting in something like Figure 9-46, which is the result of the following code:

> 假设你有一个平铺背景的文档，它看起来就像平铺过的一样，“h1”和“h2”元素都有相同的模式，只是颜色不同。“body”和标题元素都设置了固定的背景，结果如图 9-46 所示，这是以下代码的结果:

```css
body {
  background-image: url(grid1.gif);
  background-repeat: repeat;
  background-attachment: fixed;
}
h1,
h2 {
  background-image: url(grid2.gif);
  background-repeat: repeat;
  background-attachment: fixed;
}
```

How is this perfect alignment possible? Remember, when a background is fixed, the origin element is positioned with respect to the `viewport`. Thus, both background patterns begin tiling from the top-left corner of the viewport, not from the individual elements. For the `body`, you can see the entire repeat pattern. For the `h1`, however, the only place you can see its background is in the padding and content of the `h1` itself. Since both background images are the same size, and they have precisely the same origin, they appear to line up, as shown in Figure 9-46.

> 这种完美的结合是如何可能的呢?请记住，当背景是固定的，原点元素是相对于“viewport”定位的。因此，两个背景模式都是从视图的左上角开始平铺的，而不是从单个元素开始。对于“body”，您可以看到整个重复模式。然而，对于“h1”，你能看到它的背景的唯一地方是“h1”本身的填充和内容。由于两个背景图像大小相同，而且它们的原点完全相同，所以它们看起来是对齐的，如图 9-46 所示。

<Figures figure="9-46">Perfect alignment of backgrounds</Figures>

This capability can be used to create some very sophisticated effects. One of the most famous examples is the “complexspiral distorted” demonstration (http://bit.ly/meyercomplexspiral), shown in Figure 9-47.

> 这个功能可以用来创建一些非常复杂的效果。最著名的例子之一是“复杂螺旋扭曲”演示，如图 9-47 所示。

<Figures figure="9-47">The complexspiral distorted</Figures>

The visual effects are caused by assigning different fixed-attachment background images to nonbody elements. The entire demo is driven by one HTML document, four JPEG images, and a stylesheet. Because all four images are positioned in the top-left corner of the browser window but are visible only where they intersect with their elements, the images line up to create the illusion of translucent rippled glass.

> 视觉效果是由分配不同的固定附件背景图像的非身体元素。整个演示由一个 HTML 文档、四个 JPEG 图像和一个样式表驱动。因为这四张图片都位于浏览器窗口的左上角，但是只能在它们与元素相交的地方看到，所以这些图片排成一行，营造出半透明的波纹玻璃的错觉。

It is also the case that in paged media, such as printouts, every page generates its own viewport. Therefore, a fixed-attachment background should appear on every page of the printout. This could be used for effects such as watermarking all the pages in a document:

> 在分页媒体(如打印输出)中，每个页面都生成自己的视图。因此，一个固定的附件背景应该出现在打印输出的每个页面上。这可以用于效果，如水印的所有页面在一个文件:

<Tips tips="orange">Unfortunately, placing a fixed-attachment background on each page in paged media was poorly supported as of late 2017, and most browsers don’t print background images by default in any case.</Tips>

### 9.2.8 Sizing Background Images

Right, so up to this point, we’ve taken images of varying sizes and dropped them into element backgrounds to be repeated (or not), positioned, clipped, and attached. In every case, we just took the image at whatever intrinsic size it was (with the automated exception of `round` repeating). Ready to actually change the size of the origin image and all the tiled images that spawn from it?

> 好的，到目前为止，我们已经拍摄了不同大小的图像，并将它们放入元素背景中进行重复(或不重复)、定位、剪切和附加。在每一种情况下，我们只是取图像的固有大小(除了“循环”重复的自动例外)。准备好改变原始图像的大小了吗?

<Cards cards="background-size" />

Let’s start by explicitly resizing a background image. We’ll drop in an image that’s 200 × 200 pixels and then resize it to be twice as big, as shown in Figure 9-48, which is the result of the following code:

> 我们先来显式地调整背景图像的大小。我们将放入一个 200×200 像素的图像，然后将其调整为两倍大，如图 9-48 所示，这是以下代码的结果:

```css
main {
  background-image: url(yinyang.png);
  background-repeat: no-repeat;
  background-position: center;
  background-size: 400px 400px;
}
```

<Figures figure="9-48">Resizing the origin image</Figures>

You could just as easily resize the origin image to be smaller, and you aren’t confined to pixels. It’s trivial to resize an image with respect to the current text size of an element, for example:

> 你可以很容易地调整原始图像的大小，使其更小，而不局限于像素。根据元素当前的文本大小来调整图像的大小是很简单的，例如:

```css
main {
  background-image: url(yinyang.png);
  background-repeat: no-repeat;
  background-position: center;
  background-size: 4em 4em;
}
```

You can mix things up if you like, and in the process squeeze or stretch the origin image:

> 你可以混合的东西，如果你喜欢，并在过程中挤压或拉伸原始图像:

```css
main {
  background-image: url(yinyang.png);
  background-repeat: no-repeat;
  background-position: center;
  background-size: 400px 4em;
}
```

And as you might expect, if you allow the image to repeat, then all the repeated images will be the same size as the origin image. This and the previous example are both illustrated in Figure 9-49, which is the result of the following code:

> 正如你所期望的，如果你允许图像重复，那么所有重复的图像将与原始图像大小相同。这个例子和前面的例子都在图 9-49 中有说明，图 9-49 是以下代码的结果:

```css
main {
  background-image: url(yinyang.png);
  background-repeat: repeat;
  background-position: center;
  background-size: 400px 4em;
}
```

<Figures figure="9-49">Distorting the origin image by resizing it</Figures>

As that last example shows, when there are two values for `background-size`--the first is the horizontal size and the second is the vertical. (As per usual for CSS.)

> 如最后一个示例所示，当“background-size”有两个值时——第一个是水平大小，第二个是垂直大小。(和 CSS 一样。)

Percentages are a little more interesting. If you declare a percentage value, then it’s calculated with respect to the background positioning area; that is, the area defined by `background-origin`, and `not` by `background-clip`. Suppose you want an image that’s half as wide and half as tall as its background positioning area, as shown in Figure 9-50:

> 百分比更有趣一些。如果你声明一个百分比值，那么它是根据背景定位区域计算的;也就是说，由“背景-起点”定义的区域，而不是由“背景-剪辑”定义的区域。假设您想要一个图像的一半宽，一半高的背景定位区域，如图 9-50 所示:

```css
main {
  background-image: url(yinyang.png);
  background-repeat: no-repeat;
  background-position: center;
  background-size: 50% 50%;
}
```

<Figures figure="9-50">Resizing the origin image with percentages</Figures>

And yes, you can mix lengths and percentages:

> 是的，你可以混合长度和百分比:

```css
main {
  background-image: url(yinyang.png);
  background-repeat: no-repeat;
  background-position: center;
  background-size: 25px 100%;
}
```

<Tips tips="blue">Negative length and percentage values are not permitted for background-size.</Tips>

Now, what about the default value of `auto`? First off, in a case where the there’s only one value, it’s taken for the horizontal size, and the vertical size is set to `auto`. (Thus `background-size: auto` is equivalent to `background-size: auto auto`.) If you want to size the origin image vertically and leave the horizontal size to be automatic, thus preserving the intrinsic aspect ratio of the image, you have to write it explicitly, like this:

> 那么“auto”的默认值是多少呢?首先，在只有一个值的情况下，它被取为水平大小，而垂直大小被设置为“auto”。(因此，“background-size: auto”等同于“background-size: auto auto”。)如果你想要垂直地调整原始图像的大小，而保持水平图像的大小是自动的，从而保持图像的固有的高宽比，你必须明确地写它，像这样:

```css
background-size: auto 333px;
```

But what does `auto` actually do? There’s a three-step fallback process:

> 但是“自动”实际上是做什么的呢?有一个三步的后退过程:

1. If one axis is set to `auto` and the other is not, `and` the image has an intrinsic height-to-width ratio, then the `auto` axis is calculated by using the size of the other axis and the intrinsic ratio of the image. Thus, an image that’s 300 pixels wide by 200 pixels tall (a 3:2 ratio) and that is set to `background-size: 100px;` would be resized to be 100 pixels wide and 66.6667 pixels tall. If the declaration is changed to `background-size: auto 100px;`, then the image will be resized to 150 pixels wide by 100 pixels tall. This will happen for all raster images (GIF, JPEG, PNG, etc.), which have intrinsic ratios due to the nature of their image formats. This is also true of SVG images that have explicitly declared sizing information inside the file.
2. If the first step fails for some reason, but the image has an intrinsic size, then `auto` is set to be the same as the intrinsic size of that axis. Suppose you have an image with an intrinsic size of 300 pixels wide by 200 pixels tall that somehow fails to have an intrinsic ratio. In that case, `background-size: auto 100px;` would result in a size of 300 pixels wide by 100 pixels tall.
3. If the first and second steps both fail for whatever reason, then `auto` resolves to `100%`. Thus, an image with no intrinsic size that’s set to `background-size: auto 100px;` would be resized to be as wide as the background positioning area and 100 pixels tall. This can happen fairly easily with vector images like SVGs when they don’t contain explicit sizing information, and is always the case for CSS gradient images (covered in detail in “Gradients” on page 450).

---

> 1. 如果一个轴被设置为“自动”，而另一个不是，并且“图像有一个固有的高宽比，那么“自动”轴是通过使用另一个轴的大小和图像的固有比来计算的。因此，将 300 像素宽、200 像素高的图像(3:2 的比例)设置为“background-size: 100px;”将调整为 100 像素宽、66.6667 像素高。如果声明被更改为“background-size: auto 100px;”，那么图像将被调整为 150 像素宽，100 像素高。这将发生在所有的栅格图像(GIF、JPEG、PNG 等)，由于其图像格式的性质，这些图像具有固有的比率。对于在文件中显式声明大小信息的 SVG 图像也是如此。
> 2. 如果第一步由于某种原因失败，但是图像有一个固有大小，那么“auto”被设置为与该轴的固有大小相同。假设您有一个图像的固有大小是 300 像素宽，200 像素高，但不知为什么却没有一个固有比率。在这种情况下，“background-size: auto 100px;”的结果是 300 像素宽，100 像素高。
> 3. 如果第一步和第二步不管什么原因都失败了，那么“auto”将解析为“100%”。因此，如果没有设置“background-size: auto 100px;”的内景尺寸，则会被调整为与背景定位区域一样宽、100 像素高。当矢量图像(如 SVGs)不包含显式的大小信息时，这种情况很容易发生，对于 CSS 渐变图像(在 450 页的“Gradients”中有详细介绍)总是如此。

As you can see from this process, in many ways, `auto` in `background-size` acts a lot like the `auto` values of `height` and `width` act when applied to replaced elements such as images. That is to say, you’d expect roughly similar results from the following two rules, if they were applied to the same image in different contexts:

> 从这个过程中可以看到，在' background-size '中的' auto '在应用到图像等替换元素时，其作用与' height '和' width '的' auto '值非常相似。也就是说，如果你将以下两条规则应用于同一幅图像的不同上下文中，你会得到大致相似的结果:

```css
img.yinyang {
  width: 300px;
  height: auto;
}
main {
  background-image: url(yinyang.png);
  background-repeat: no-repeat;
  background-size: 300px auto;
}
```

#### Covering and containing

Now for the real fun! Suppose you have an image that you want to cover the entire background of an element, and you don’t care if parts of it stick outside the background painting area. In this case, you can use `cover`, as shown in Figure 9-51, which is the result of the following code:

> 现在是真正的乐趣!假设您有一个想要覆盖一个元素的整个背景的图像，并且您不关心它的一部分是否粘附在背景绘制区域之外。在这种情况下，可以使用“cover”，如图 9-51 所示，它是以下代码的结果:

```css
main {
  background-image: url(yinyang.png);
  background-position: center;
  background-size: cover;
}
```

<Figures figure="9-51">Covering the background with the origin image</Figures>

This scales the origin image so that it completely covers the background positioning area while still preserving its intrinsic aspect ratio, assuming it has one. You can see an example of this in Figure 9-52, where a 200 × 200 pixel image is scaled up to cover the background of an 800 × 400 pixel element, which is the result of the following code:

> 这样可以缩放原始图像，使其完全覆盖背景定位区域，同时仍然保持其固有的高宽比(假设它有一个)。你可以在图 9-52 中看到一个这样的例子，一个 200×200 像素的图像被放大来覆盖一个 800×400 像素的元素的背景，这是以下代码的结果:

```css
main {
  width: 800px;
  height: 400px;
  background-image: url(yinyang.png);
  background-position: center;
  background-size: cover;
}
```

Note that there was no `background-repeat` in that example. That’s because we expect the image to fill out the entire background, so whether it’s repeated or not doesn’t really matter.

> 注意，在这个示例中没有“background-repeat”。这是因为我们期望图像填充整个背景，所以它是否重复并不重要。

You can also see that `cover` is very much different than `100% 100%`. If we’d used `100% 100%`, then the origin image would have been stretched to be 800 pixels wide by 400 pixels tall. Instead, `cover` made it 800 pixels wide and tall, then centered the image inside the background positioning area. This is the same as if we’d said `100% auto` in this particular case, but the beauty of `cover` is that it works regardless of whether your element is wider than it is tall, or taller than it is wide.

> 你也可以看到“cover”和“100% 100%”是非常不同的。如果我们使用“100% 100%”，那么原始图像将被拉伸到 800 像素宽，400 像素高。相反，“cover”将它设置为 800 像素宽和高，然后将图像居中到背景定位区域。这和我们在这个例子中所说的“100% auto”是一样的，但是“cover”的美妙之处在于不管你的元素是宽是高，还是高是宽，它都能工作。

<Figures figure="9-52">Covering the background with the origin image, redux</Figures>

By contrast, `contain` will scale the image so that it fits exactly inside the background positioning area, even if that leaves some of the rest of the background showing around it. This is illustrated in Figure 9-53, which is the result of the following code:

> 相比之下，“包含”将缩放图像，使其正好适合背景定位区域，即使这样会留下一些其余的背景显示在它周围。如图 9-53 所示，这是以下代码的结果:

```css
main {
  width: 800px;
  height: 400px;
  background-image: url(yinyang.png);
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
}
```

<Figures figure="9-53">Containing the origin image within the background</Figures>

In this case, since the element is shorter than it is tall, the origin image was scaled so it was as tall as the background positioning area, and the width was scaled to match, just as if we’d declared `auto 100%`. If an element is taller than it is wide, then `contain` acts like `auto 100%`.

> 在本例中，由于元素的长度小于它的长度，因此对原始图像进行了缩放，使其与背景定位区域一样高，并对宽度进行了缩放以匹配，就像我们声明的“auto 100%”一样。如果一个元素比它的宽度高，那么“包含”就像“自动 100%”。

You’ll note that we brought `no-repeat` back to the example so that things wouldn’t become too visually confusing. Removing that declaration would cause the background to repeat, which is no big deal if that’s what you want. The result is shown in Figure 9-54.

> 您会注意到，我们将“no-repeat”带回到示例中，这样在视觉上就不会太混乱。删除该声明将导致后台重复，如果您希望这样做，这也没什么大不了的。结果如图 9-54 所示。

<Figures figure="9-54">Repeating a contained origin image</Figures>

Always remember: the sizing of `cover` and `contain` images is always with respect to the background positioning area, which is defined by `background-origin`. This is true even if the background painting area defined by `background-clip` is different!

> 始终记住:“封面”和“包含”图像的大小始终与背景定位区域相关，这是由“背景-原点”定义的。这是真的，即使“background-clip”定义的背景绘画区域不同!

Consider the following rules, which are depicted in Figure 9-55:

> 考虑以下规则，如图 9-55 所示:

```css
div {
  border: 1px solid red;
  background: green url(yinyang-sm.png) center no-repeat;
}
.cover {
  background-size: cover;
}
.contain {
  background-size: contain;
}
.clip-content {
  background-clip: content-box;
}
.clip-padding {
  background-clip: padding-box;
}
.origin-content {
  background-origin: content-box;
}
.origin-padding {
  background-origin: padding-box;
}
```

<Figures figure="9-55">Covering, containing, positioning, and clipping</Figures>

Yes, you can see background color around the edges of some of those, and others get clipped. That’s the difference between the painting area and the positioning area. You’d think that `cover` and `contain` would be sized with respect to the painting area, but they aren’t. Keep that firmly in mind whenever you use these values.

> 是的，你可以看到一些边缘的背景色，还有一些被剪掉了。这就是绘制区域和定位区域的区别。你可能会认为“覆盖”和“包含”的大小应该与绘画区域的大小相对应，但事实并非如此。当您使用这些值时，请牢记这一点。

<Tips tips="blue">In this section, I used raster images (GIFs, to be precise) even though they tend to look horrible when scaled up and represent a waste of network resources when scaled down. (I did this so that it would be extra obvious when lots of up-scaling was happening.) This is an inherent risk in scaling background raster images. On the other hand, you can just as easily use SVGs as background images, and they scale up or down with no loss of quality or waste of bandwidth. Once upon a time, SVGs were unusable because browsers didn’t support them, but those days are long past. If you’re going to be scaling a background image and it doesn’t have to be a photograph, strongly consider using SVG.</Tips>

### 9.2.9 Bringing It All Together

As is often the case with thematic areas of CSS, the background properties can all be brought together in a single shorthand property: `background`. Whether you might want to do that is another question entirely.

> 就像 CSS 的主题区域一样，背景属性都可以放在一个简单的属性中:' background '。你是否想这样做完全是另一个问题。

<Cards cards="background" />

The syntax here can get a little confusing. Let’s start simple and work our way up from there.

> 这里的语法可能有点混乱。让我们从简单开始，从这里开始。

First off, the following statements are all equivalent to each other and will have the effect shown in Figure 9-56:

> 首先，下列语句都是等价的，其效果如图 9-56 所示:

```css
body {
  background-color: white;
  background-image: url(yinyang.png);
  background-position: top left;
  background-repeat: repeat-y;
  background-attachment: fixed;
  background-origin: padding-box;
  background-clip: border-box;
  background-size: 50% 50%;
}
body {
  background: white url(yinyang.png) repeat-y top left/50% 50% fixed padding-box
    border-box;
}
body {
  background: fixed url(yinyang.png) padding-box border-box white repeat-y top
    left/50% 50%;
}
body {
  background: url(yinyang.png) top left/50% 50% padding-box white repeat-y fixed
    border-box;
}
```

<Figures figure="9-56">Using shorthand</Figures>

You can mostly mix up the order of the values however you like, but there are three restrictions. The first is that any `background-size` value `must` come immediately after the `background-position` value, and must be separated from it by a solidus (`/`, the “forward slash”). Additionally, within those values, the usual restrictions apply: the horizontal value comes first, and the vertical value comes second, assuming that you’re supplying axis-derived values (as opposed to, say, `cover`).

> 您可以随意打乱值的顺序，但是有三个限制。首先，任何“background-size”值必须紧跟在“background-position”值之后，并且必须用一个 solidus(' / '，即“正斜线”)将其分隔开。此外，在这些值中还应用了通常的限制:首先是水平值，然后是垂直值，假设您提供的是轴向派生的值(而不是“cover”)。

The last restriction is that if you supply values for both `background-origin` and `background-clip`, the first of the two you list will be assigned to `background-origin`, and the second to `background-clip.` That means that the following two rules are functionally identical:

> 最后一个限制是，如果您同时为' background-origin '和' background-clip '提供值，那么您列出的两个值中的第一个将被赋给' background-origin '，第二个赋给' background-clip '。这意味着以下两条规则在功能上是相同的:

```css
body {
  background: url(yinyang.png) top left/50% 50% padding-box border-box white
    repeat-y fixed;
}
body {
  background: url(yinyang.png) top left/50% 50% padding-box white repeat-y fixed
    border-box;
}
```

Related to that, if you only supply one such value, it sets both `background-origin` and `background-clip`. Thus, the following shorthand sets both the background positioning area and the background painting area to the padding box:

> 与此相关的是，如果您只提供一个这样的值，它将同时设置“background-origin”和“background-clip”。因此，下面的速记设置背景定位区域和背景绘画区域到填充框:

```css
body {
  background: url(yinyang.png) padding-box top left/50% 50% border-box;
}
```

As is the case for shorthand properties, if you leave out any values, the defaults for the relevant properties are filled in automatically. Thus, the following two are equivalent:

> 与简写属性一样，如果省略任何值，相关属性的默认值将自动填充。因此，以下两者是等价的:

```css
body {
  background: white url(yinyang.png;}
body {background: white url(yinyang.png) transparent 0% 0%/auto repeat
 scroll padding-box border-box;
}
```

Even better, there are no required values for `background`—as long as you have at least one value present, you can omit the rest. It’s possible to set just the background color using the shorthand property, which is a very common practice:

> 更好的是，“背景”不需要任何值——只要有至少一个值存在，就可以省略其余的值。可以使用速记属性设置背景颜色，这是一个非常常见的做法:

```css
body {
  background: white;
}
```

On that note, remember that `background` is a shorthand property, and, as such, its default values can obliterate previously assigned values for a given element. For example:

> 在这一点上，请记住“background”是一个简写属性，因此，它的默认值可以删除之前为给定元素分配的值。例如:

```css
h1,
h2 {
  background: gray url(thetrees.jpg) center/contain repeat-x;
}
h2 {
  background: silver;
}
```

Given these rules, `h1` elements will be styled according to the first rule. `h2` elements will be styled according to the second, which means they’ll just have a flat silver background. No image will be applied to `h2` backgrounds, let alone centered and repeated horizontally. It is more likely that the author meant to do this:

> 根据这些规则，“h1”元素将根据第一条规则进行样式化。“h2”元素将根据第二种样式进行样式化，这意味着它们将只有一个扁平的银色背景。没有图像将被应用到“h2”背景，更不用说居中和水平重复。作者更有可能这样做:

```css
h1,
h2 {
  background: gray url(thetrees.jpg) center/contain repeat-x;
}
h2 {
  background-color: silver;
}
```

This lets the background color be changed without wiping out all the other values.

> 这样就可以改变背景颜色，而不会清除所有其他值。

There’s one more restriction that will lead us very neatly into the next section: you can only supply a background color on the final background layer. No other background layer can have a solid color declared. What the heck does that mean? So glad you asked.

> 还有一个限制将引导我们非常整洁地进入下一节:您只能在最后的背景层上提供背景颜色。没有其他的背景层可以有一个纯色声明。这到底是什么意思?很高兴你问了这个问题。

### 9.2.10 Multiple Backgrounds

Throughout most of this chapter, I’ve been gliding right past the fact that almost all the background properties accept a comma-separated list of values. For example, if you wanted to have three different background images, you could do it like this:

> 在本章的大部分内容中，我一直忽略了这样一个事实:几乎所有的背景属性都接受逗号分隔的值列表。例如，如果你想有三个不同的背景图片，你可以这样做:

```css
section {
  background-image: url(bg01.png), url(bg02.gif), url(bg03.jpg);
  background-repeat: no-repeat;
}
```

Seriously. It will look like what we see in Figure 9-57.

> 认真对待。它将与我们在图 9-57 中看到的类似。

<Figures figure="9-57">Multiple background images</Figures>

This creates three background layers, one for each image. Technically, it’s two background layers and a final background layer, which is the third in this series of three.

> 这就创建了三个背景层，每个图像一个。从技术上讲，它是两个背景层和最后一个背景层，后者是本系列的第三个。

As we saw in Figure 9-57, the three images were piled into the top-left corner of the element and didn’t repeat. The lack of repetition is because we declared `backgroundrepeat: no-repeat`, and the top-left positioning is because the default value of background-position is `0% 0%` (the top-left corner). But suppose we want to put the first image in the top right, put the second in the center left, and put the last layer in the center bottom? We can also layer `background-position`, as shown in Figure 9-58, which is the result of the following code:

> 正如我们在图 9-57 中看到的，这三个图像被堆积在元素的左上角，并且没有重复。缺少重复是因为我们声明了“backgroundrepeat: no-repeat”，而左上角的定位是因为 backgroundposition 的默认值是“0% 0%”(左上角)。但是假设我们想把第一个图像放在右上角，把第二个图像放在中间左边，把最后一个图层放在中间底部?我们还可以分层“background-position”，如图 9-58 所示，这是以下代码的结果:

```css
section {
  background-image: url(bg01.png), url(bg02.gif), url(bg03.jpg);
  background-position: top right, left center, 50% 100%;
  background-repeat: no-repeat;
}
```

<Figures figure="9-58">Individually positioning background images</Figures>

Now, suppose we want to keep the first two from repeating, but horizontally repeat the third:

> 现在，假设我们想要避免前两个重复，但是水平地重复第三个:

```css
section {
  background-image: url(bg01.png), url(bg02.gif), url(bg03.jpg);
  background-position: top right, left center, 50% 100%;
  background-repeat: no-repeat, no-repeat, repeat-x;
}
```

Nearly every background property can be comma-listed this way. You can have different origins, clipping boxes, sizes, and just about everything else for each background layer you create. Technically, there is no limit to the number of layers you can have, though at a certain point it’s just going to get silly.

> 几乎每个背景属性都可以通过这种方式被逗号列出。对于创建的每个背景层，可以有不同的起点、剪切框、大小和几乎所有其他东西。从技术上讲，你可以拥有的层数是没有限制的，尽管在某种程度上它会变得很傻。

Even the shorthand `background` can be comma-separated. The following example is exactly equivalent to the previous one, and the result is shown in Figure 9-59:

> 即使是速记的“背景”也可以用逗号分隔。下面的例子与前一个完全相同，结果如图 9-59 所示:

```css
section {
  background: url(bg01.png) right top no-repeat, url(bg02.gif) center left
      no-repeat, url(bg03.jpg) 50% 100% repeat-x;
}
```

<Figures figure="9-59">Multiple background layers via shorthand</Figures>

The only real restriction on multiple backgrounds is that `background-color` does `not` repeat in this manner, and if you provide a comma-separated list for the `background` shorthand, then the color can only appear on the last background layer. If you add a color to any other layer, the entire `background` declaration is made invalid. Thus, if we wanted to have a green background fill for the previous example, we’d do it in one of the following two ways:

> 对多个背景的唯一实际限制是“background-color”不以这种方式重复，如果您为“background”简写提供一个逗号分隔的列表，那么颜色只能出现在最后一个背景层上。如果你给其他图层添加颜色，整个“背景”声明将无效。因此，如果我们想要在前面的例子中使用绿色背景填充，我们可以使用以下两种方法之一:

```css
section {
  background: url(bg01.png) right top no-repeat, url(bg02.gif) center left
      no-repeat, url(bg03.jpg) 50% 100% repeat-x green;
}
section {
  background: url(bg01.png) right top no-repeat, url(bg02.gif) center left
      no-repeat, url(bg03.jpg) 50% 100% repeat-x;
  background-color: green;
}
```

The reason for this restriction is pretty straightforward. Imagine if you were able to add a full background color to the first background layer. It would fill in the whole background and obscure all the background layers behind it! So if you do supply a color, it can only be on the last layer, which is “bottom-most.”

> 这个限制的原因很简单。想象一下，如果你能够为第一个背景层添加一个完整的背景色。它将填充整个背景，并掩盖它背后的所有背景层!所以如果你提供了一种颜色，它只能在最后一层，也就是“最下面的一层”。

This ordering is important to internalize as soon as possible, because it runs counter to the instincts you’ve likely built up in the course of using CSS. After all, you know what will happen here: the `h1` background will be green:

> 这种顺序对于尽快将其内在化是很重要的，因为它与您在使用 CSS 过程中可能形成的直觉背道而驰。毕竟，你知道这里会发生什么:“h1”背景将是绿色的:

```css
h1 {
  background-color: red;
}
h1 {
  background-color: green;
}
```

Contrast that with this multiple-background rule, which will make the `h1` background red, as shown in Figure 9-60:

> 与此相反，这个多重背景规则将使“h1”背景为红色，如图 9-60 所示:

```css
h1 {
  background: url(box-red.gif), url(box-green.gif) green;
}
```

<Figures figure="9-60">The order of background layers</Figures>

Yes, red. The red GIF is tiled to cover the entire background area, as is the green GIF, but the red GIF is “on top of ” the green GIF. It’s closer to you. And the effect is exactly backward from the “last one wins” rules built into the cascade.

> 是的,红色的。红色的 GIF 被平铺到整个背景区域，绿色的 GIF 也是如此，但是红色的 GIF“盖在”绿色的 GIF 上面。它离你更近。而且这种效果与瀑布中内置的“最后赢家”规则正好相反。

I visualize it like this: when there are multiple backgrounds, they’re listed like the layers in a drawing program such as Photoshop or Illustrator. In the layer palette of a drawing program, layers at the top of the palette are drawn over the layers at the bottom. It’s the same thing here: the layers listed at the top of the list are drawn over the layers at the bottom of the list.

> 我把它想象成这样:当有多个背景时，它们就像绘图程序(如 Photoshop 或 Illustrator)中的图层一样被列出。在绘图程序的层调色板中，调色板顶部的层被绘制在底部的层上。这里是一样的:列表顶部列出的层被绘制在列表底部的层上。

The odds are pretty good that you will, at some point, set up a bunch of background layers in the wrong order, because your cascade-order reflexes will kick in. (This error still gets me from time to time, so don’t beat yourself up if it gets you.)

> 很有可能，在某个时候，你会以错误的顺序设置一堆背景层，因为你的级联级反射会起作用。(这个错误仍然时不时地困扰着我，所以如果它困扰着你，不要自责。)

Another fairly common mistake when you’re getting started with multiple backgrounds is to forget to turn off background tiling for your background layers, thus obscuring all but the top layer. See Figure 9-61, for example, which is the result of the following code:

> 在开始使用多个背景时，另一个常见的错误是忘记关闭背景图层的背景平铺，从而模糊了除顶层之外的所有层。例如，参见图 9-61，它是以下代码的结果:

```css
section {
  background-image: url(bg02.gif), url(bg03.jpg);
}
```

<Figures figure="9-61">Obscuring layers with repeated images</Figures>

We can only see the top layer because it’s tiling infinitely, thanks to the default value of `background-repeat`. That’s why the example at the beginning of this section had a `background-repeat: no-repeat`. But how did the browser know to apply that single repeat value to all the layers? Because CSS defines an algorithm for filling in the missing pieces.

> 我们只能看到顶层，因为它是无限平铺的，这要感谢默认值“background-repeat”。这就是为什么本节开头的示例有一个“background-repeat: no-repeat”。但是浏览器是如何知道将单个的 repeat 值应用到所有层的呢?因为 CSS 定义了一种填充缺失部分的算法。

#### Filling in missing values

Multiple backgrounds are cool and all, but what happens if you forget to supply all the values for all the layers? For example, what happens with background clipping in this code?

> 多重背景很酷，但是如果你忘记为所有的图层提供所有的值会怎么样呢?例如，这段代码中的背景剪辑会发生什么?

```css
section {
  background-image: url(bg01.png), url(bg02.gif), url(bg03.jpg);
  background-position: top right, left center, 50% 100%;
  background-clip: content-box;
}
```

What happens is that the declared value is filled in for the missing values, so the preceding code is functionally equivalent to this:

> 所发生的是，声明的值填补了缺失的值，所以前面的代码在功能上等价于这个:

```css
section {
  background-image: url(bg01.png), url(bg02.gif), url(bg03.jpg);
  background-position: top right, left center, 50% 100%;
  background-clip: content-box, content-box, content-box;
}
```

All right, great. But then someone comes along and adds a background layer by adding another image. Now what?

> 好了,好了。但后来有人来了，通过添加另一张图片添加了一个背景层。现在怎么办呢?

```css
section {
  background-image: url(bg01.png), url(bg02.gif), url(bg03.jpg), url(bg04.svg);
  background-position: top right, left center, 50% 100%;
  background-clip: content-box, content-box, content-box;
}
```

What happens is the declared set of values is repeated as many times as necessary to fill in the gaps. In this case, that means a result equivalent to declaring the following:

> 所发生的是声明的值集被重复多少次以填补空白。在这种情况下，这意味着相当于声明以下内容的结果:

```css
section {
  background-image: url(bg01.png), url(bg02.gif), url(bg03.jpg), url(bg04.svg);
  background-position: top right, left center, 50% 100%, top right;
  background-clip: content-box, content-box, content-box, content-box;
}
```

Notice how the fourth `background-position` is the same as the first? That‘s also the case for the fourth `background-clip`, though it’s not as obvious. Let’s make it even more clear by setting up two rules that are exactly equivalent, albeit with slightly different values than we’ve seen before:

> 注意到第四个“背景位置”与第一个“背景位置”是如何相同的吗?这也是第四个“背景剪辑”的情况，尽管它不那么明显。让我们通过设置两个完全相同的规则来更清楚地说明这一点，尽管与我们之前看到的值略有不同:

```css
body {
  background-image: url(bg01.png), url(bg02.gif), url(bg03.jpg), url(bg04.svg);
  background-position: top left, bottom center, 33% 67%;
  background-origin: border-box, padding-box;
  background-repeat: no-repeat;
  background-color: gray;
}
body {
  background-image: url(bg01.png), url(bg02.gif), url(bg03.jpg), url(bg04.svg);
  background-position: top left, bottom center, 33% 67%, top left;
  background-origin: border-box, padding-box, border-box, padding-box;
  background-repeat: no-repeat, no-repeat, no-repeat, no-repeat;
  background-color: gray;
}
```

That’s right: the color didn’t get repeated, because there can only be one background color!

> 没错:颜色没有重复，因为只有一个背景色!

If we take away two of the background images, then the leftover values for the others will be ignored. Again, two rules that are exactly the same in effect:

> 如果我们去掉两个背景图像，那么剩下的值将被忽略。同样，有两条规则实际上是完全相同的:

```css
body {
  background-image: url(bg01.png), url(bg04.svg);
  background-position: top left, bottom center, 33% 67%;
  background-origin: border-box, padding-box;
  background-repeat: no-repeat;
  background-color: gray;
}
body {
  background-image: url(bg01.png), (bg04.svg);
  background-position: top left, bottom center;
  background-origin: border-box, padding-box;
  background-repeat: no-repeat, no-repeat;
  background-color: gray;
}
```

Notice that I actually removed the second and third images (`bg02.gif` and `bg03.jpg`). Since this left two images, the third value of `background-position` was dropped. The browser doesn’t remember what CSS you had last time, and certainly doesn’t (because it can’t) try to maintain parallelism between the old values and the new ones. If you cut values out of the middle of `background-image`, you have to drop or rearrange values in other properties to keep up.

> 请注意，我实际上删除了第二和第三张图片(' bg02。gif”和“bg03.jpg”)。因为还剩下两张图片，所以第三个“背景位置”的值被去掉了。浏览器不记得上次使用了什么 CSS，当然也不会(因为它不能)尝试保持新旧值之间的并行性。如果从“background-image”的中间删除值，则必须删除或重新排列其他属性中的值才能跟上。

The easy way to avoid these sorts of situations is just to use `background`, like so:

> 避免这类情况的简单方法就是使用“background”，就像这样:

```css
body {
  background: url(bg01.png) top left border-box no-repeat, url(bg02.gif) bottom
      center padding-box no-repeat,
    url(bg04.svg) bottom center padding-box no-repeat gray;
}
```

That way, when you add or subtract background layers, the values you meant to apply specifically to them will come in or go out with them. This can mean some annoying repetition if all the backgrounds should have the same value of a given property, like `background-origin`. If that’s the situation, you can blend the two approaches, like so:

> 这样，当您添加或删除背景层时，您想要专门应用于它们的值将与它们一起输入或输出。如果所有的背景都具有相同的给定属性值，比如“background-origin”，这可能意味着一些烦人的重复。如果是这种情况，你可以混合这两种方法，就像这样:

```css
body {
  background: url(bg01.png) top left no-repeat, url(bg02.gif) bottom center
      no-repeat, url(bg04.svg) bottom center no-repeat gray;
  background-origin: padding-box;
}
```

This works just as long as you don’t need to make any exceptions. The minute you decide to change the origin of one of those background layers, then you’ll need to explicitly list them, however you do it.

> 只要您不需要做任何异常，这种方法就可以工作。当您决定更改其中一个背景层的原点时，无论如何都需要显式地列出它们。

Remember that the number of layers is determined by the number of background images, and so, by definition, `background-image` values are `not` repeated to equal the number of comma-separated values given for other properties. You might want to put the same image in all four corners of an element and think you could do it like this:

> 请记住，层的数量是由背景图像的数量决定的，因此，根据定义，“background-image”值“not”重复等于其他属性的逗号分隔值的数量。你可能想把同样的图像放在一个元素的四个角落，你可以这样做:

```css
background-image: url(i/box-red.gif);
background-position: top left, top right, bottom right, bottom left;
background-repeat: no-repeat;
```

The result, however, would be to place a single red box in the top-left corner of the element. In order to get images in all four corners, as shown in Figure 9-62, you’ll have to list the same image four times:

> 但是，结果将在元素的左上角放置一个红色框。为了得到所有四个角落的图像，如图 9-62 所示，您必须列出相同的图像四次:

```css
background-image: url(i/box-red.gif), url(i/box-red.gif), url(i/box-red.gif),
  url(i/box-red.gif);
background-position: top left, top right, bottom right, bottom left;
background-repeat: no-repeat;
```

<Figures figure="9-62">Placing the same image in all four corners</Figures>

## 9.3 Gradients

There are two new image types defined by CSS that are described entirely in CSS: linear gradients and radial gradients. Of each type, there are two sub-types: repeating and non-repeating. Gradients are most often used in backgrounds, which is why they’re being covered here, though they can be used in any context where an image is permitted—`list-style-image`, for example.

> CSS 定义了两种新的图像类型，它们完全在 CSS 中描述:线性梯度和径向梯度。每种类型都有两种子类型:重复和非重复。渐变最常用于背景，这就是为什么在这里介绍它们的原因，尽管它们可以用于任何允许使用图像的环境中——例如“列表样式图像”。

A gradient is just a smooth visual transition from one color to another. For example, a gradient from white to black will start white, run through successively darker shades of gray, and eventually arrive at black. How gradual or abrupt a transition that is depends on how much space the gradient has to operate. If you run from white to black over 100 pixels, then each pixel along the gradient’s progression will be another 1% darker gray. This is diagrammed in Figure 9-63.

> 渐变就是从一种颜色到另一种颜色的平滑视觉过渡。例如，从白色到黑色的渐变将从白色开始，依次经过较深的灰色阴影，最终到达黑色。这种转变是渐进的还是突然的，取决于梯度作用的空间大小。如果你从白色到黑色超过 100 像素，那么沿着梯度的每个像素的进展将是另一个 1%的深灰色。这是在图 9-63 中绘制的。

<Figures figure="9-63">The progression of a simple gradient</Figures>

As we go through the process of exploring gradients, always keep this in mind: `gradients are images`. It doesn’t matter that you describe them by typing CSS—they are every bit as much images as SVGs, PNG, GIFs, and so on.

> 当我们在探索梯度的过程中，始终要记住:“梯度是图像”。您可以通过输入 css 来描述它们，这并不重要—它们与 svg、PNG、gif 等一样多。

What’s interesting about gradients is that they have no intrinsic dimensions, which means that if the `background-size` property’s value `auto` is used, it is treated as if it were `100%`. Thus, if you don’t define a `background-size` for a background gradient, it will be set to the default value of `auto`, which is the same as declaring 100% 100%. So, by default, background gradients fill in the entire background positioning area.

> 梯度的有趣之处在于它们没有内在维度，这意味着如果使用“background-size”属性的值“auto”，它就会被视为“100%”。因此，如果你没有为背景渐变定义一个“background-size”，它将被设置为“auto”的默认值，这和声明 100% 100%是一样的。因此，默认情况下，背景渐变会填充整个背景定位区域。

### 9.3.1 Linear Gradients

Linear gradients are gradient fills that proceed along a linear vector, referred to as the `gradient line`. They can be anything but simple, however. Here are a few relatively simple gradients, with the results shown in Figure 9-64:

> 线性梯度是沿着线性向量的梯度填充，称为“梯度线”。然而，它们绝不是简单的。下面是一些相对简单的梯度，结果如图 9-64 所示:

```css
#ex01 {
  background-image: linear-gradient(purple, gold);
}
#ex02 {
  background-image: linear-gradient(90deg, purple, gold);
}
#ex03 {
  background-image: linear-gradient(to left, purple, gold);
}
#ex04 {
  background-image: linear-gradient(-135deg, purple, gold, navy);
}
#ex05 {
  background-image: linear-gradient(to bottom left, purple, gold, navy);
}
```

<Figures figure="9-64">Simple linear gradients</Figures>

The first of these is the most basic that a gradient can be: two colors. This causes a gradient from the first color at the top of the background positioning area to the second color at the bottom of the background positioning area.

> 第一个是最基本的渐变:两种颜色。这将导致从背景定位区域顶部的第一种颜色到背景定位区域底部的第二种颜色的渐变。

The gradient goes from top to bottom because the default direction for gradients is `to bottom`, which is the same as `180deg` and its various equivalents (for example, `0.5turn`). If you’d like to go a different direction, then you can start the gradient value with a direction. That’s what was done for all the other gradients shown in Figure 9-64.

> 梯度从上到下，因为梯度的默认方向是“到下”，这是相同的“180 度”及其各种等值(例如，“0.5 转”)。如果你想要一个不同的方向，那么你可以开始一个方向的梯度值。这就是对图 9-64 中所示的所有其他梯度所做的。

So the basic syntax of a linear gradient is:

> 所以线性梯度的基本语法是:

```css
linear-gradient(
 [[ <angle> | to <side-or-quadrant> ],]? [ <color-stop> [, <color-hint>]? ]# ,
 <color-stop>
)
```

We’ll explore both color stops and color hints very soon. For now, the basic pattern to keep in mind is: an optional direction at the start, a list of color stops and/or color hints, and a color stop at the end.

> 我们将很快探讨颜色停止和颜色提示。现在，要记住的基本模式是:在开始处有一个可选的方向，一组颜色停止和/或颜色提示，在结束处有一个颜色停止。

While you only use the `to` keyword if you’re describing a side or quadrant with keywords like `top` and `right`, the direction you give `always` describes the direction in which the gradient line points. In other words, `linear-gradient(0deg,red,green)` will have red at the bottom and green at the top because the gradient line points toward zero degrees (the top of the element) and thus ends with green. Just remember to leave out the `to` if you’re using an angle value because something like to `45deg` is invalid and will be ignored.

> 当你用“顶”和“右”这样的关键字来描述一个边或象限时，你只使用“到”这个关键字，而你给出的方向“总是”用来描述梯度线点的方向。换句话说，“linear-gradient(0deg,red,green)”将在底部显示红色，在顶部显示绿色，因为渐变线指向 0 度(元素顶部)，因此以绿色结束。如果你使用的是角度值，请记住不要使用“to”，因为“45deg”是无效的，会被忽略。

#### Gradient colors

You’re able to use any color value you like, including alpha-channel values such as `rgba()` and keywords like `transparent`. Thus it’s entirely possible to fade out pieces of your gradient by blending to (or from) a color with zero opacity. Consider the following rules, which are depicted in Figure 9-65:

> 你可以使用任何你喜欢的颜色值，包括字母通道的值如' rgba() '和关键字如'透明'。因此，完全有可能通过混合到(或从)一个零不透明度的颜色来淡出渐变部分。考虑以下规则，如图 9-65 所示:

```css
#ex01 {
  background-image: linear-gradient(
    to right,
    rgb(200, 200, 200),
    rgb(255, 255, 255)
  );
}
#ex02 {
  background-image: linear-gradient(
    to right,
    rgba(200, 200, 200, 1),
    rgba(200, 200, 200, 0)
  );
}
```

<Figures figure="9-65">Fading to white versus fading to transparent</Figures>

As you can see, the first example fades from light gray to white, whereas the second example fades the same light gray from opaque to transparent, thus allowing the parent element’s yellow background to show through.

> 如您所见，第一个示例从浅灰色渐变为白色，而第二个示例从不透明渐变为透明，从而允许父元素的黄色背景显示出来。

You’re certainly not restricted to two colors, either. You’re free to add as many colors as you can stand. Consider the following gradient:

> 你当然也不局限于两种颜色。你可以自由添加尽可能多的颜色。考虑以下梯度:

```css
#wdim {background-image: linear-gradient(90deg,
 red, orange, yellow, green, blue, indigo, violet,
 red, orange, yellow, green, blue, indigo, violet
 );
```

The gradient line points toward 90 degrees, which is the right side. There are 14 color stops in all, one for each of the comma-separated color names, and they are distributed evenly along the gradient line, with the first at the beginning of the line and the last at the end. Between the color stops, the colors are blended as smoothly as possible from one color to the other. This is shown in Figure 9-66.

> 梯度线指向 90 度，也就是右边。总共有 14 个色位，每个色位对应一个逗号分隔的色名，它们均匀地分布在渐变线上，第一个在线条的开头，最后一个在末尾。在颜色停止之间，颜色尽可能平滑地从一种颜色混合到另一种颜色。如图 9-66 所示。

<Figures figure="9-66">The distribution of color stops along the gradient line</Figures>

So, without any indication of where the color stops should be positioned, they’re evenly distributed. What happens if you give them positions?

> 因此，没有任何迹象表明颜色应该停止的位置，他们是均匀分布。如果你给他们位置会怎么样?

#### Positioning color stops

The full syntax of a `<color-stop>` is:

> `<color-stop>` 的完整语法是:

```css
<color> [ <length> | <percentage> ]?
```

After every color value, you can (but don’t have to) supply a position value. This gives you the ability to distort the usual regular progression of color stops into something else.

> 在每个颜色值之后，您可以(但不必)提供一个位置值。这使你有能力将通常的颜色停止的顺序扭曲成其他的东西。

We’ll start with lengths, since they’re pretty simple. Let’s take a rainbow progression (only a single rainbow this time) and have each color of the rainbow occur every 25 pixels, as shown in Figure 9-67:

> 我们从长度开始，因为它们很简单。让我们使用彩虹进程(这次只使用一条彩虹)，让彩虹的每种颜色每 25 个像素出现一次，如图 9-67 所示:

```css
#spectrum {
  background-image: linear-gradient(
    90deg,
    red,
    orange 25px,
    yellow 50px,
    green 75px,
    blue 100px,
    indigo 125px,
    violet 150px
  );
}
```

<Figures figure="9-67">Placing color stops every 25 pixels</Figures>

This worked out just fine, but notice what happened after 150 pixels—the violet just continued on to the end of the gradient line. That’s what happens if you set up the color stops so they don’t make it to the end of the gradient line: the last color is just carried onward.

> 这个效果很好，但是注意在 150 个像素之后发生了什么——紫色继续延伸到渐变线的末端。如果你设置了颜色停止，这样它们就不会到达渐变线的末端:最后一种颜色只是向前移动。

Conversely, if your color stops go beyond the end of the gradient line, then the gradient just stops at whatever point it manages to reach when it gets to the end of the gradient line. This is illustrated in Figure 9-68:

> 相反，如果你的颜色超过了渐变线的末端，那么渐变就会在到达渐变线末端时停止。如图 9-68 所示:

```css
#spectrum {
  background-image: linear-gradient(
    90deg,
    red,
    orange 200px,
    yellow 400px,
    green 600px,
    blue 800px,
    indigo 1000px,
    violet 1200px
  );
}
```

<Figures figure="9-68">Gradient clipping when colors stops go too far</Figures>

Since the last color stop is at 1,200 pixels but the gradient line is shorter than that, the gradient just stops right around the color `blue`. That’s as far as the gradient gets before running out of room.

> 因为最后的颜色停止点是 1200 像素，但是渐变线比那个短，所以渐变点正好在“蓝色”附近停止。这是倾斜度在空间耗尽之前的最大值。

Note that in the preceding two examples and figures, the first color (`red`) didn’t have a length value. If the first color has no position, it’s assumed to be the beginning of the gradient line. Similarly, if you leave a position off the last color stop, it’s assumed to be the end of the gradient line. (But note that this is not true for repeating gradients, which we’ll cover in the upcoming section “Repeating Gradients” on page 481.)

> 注意，在前面的两个示例和图中，第一个颜色(“red”)没有长度值。如果第一种颜色没有位置，则假定为渐变线的起点。类似地，如果在最后一个颜色停止处留下一个位置，则假定它是渐变线的末端。(但是请注意，对于重复梯度来说，这是不正确的，我们将在接下来的 481 页的“重复梯度”一节中讨论这个问题。)

You can use any length value you like, not just pixels. Ems, inches, you name it. You can even mix different units into the same gradient, although this is not generally recommended for reasons we’ll get to in a little bit. You can even have negative length values if you want; doing so will place a color stop before the beginning of the gradient line, and clipping will occur in the same manner as it happens at the end of the line, as shown in Figure 9-69:

> 您可以使用任何长度值，而不仅仅是像素。Ems，英寸，你能想到的。你甚至可以将不同的单位混合到相同的梯度中，尽管由于我们稍后会讲到的原因，通常不推荐这样做。你甚至可以有负长度值，如果你想;这样做会在渐变线的开始之前放置一个颜色停止点，裁剪会以与渐变线结束时相同的方式进行，如图 9-69 所示:

```css
#spectrum {
  background-image: linear-gradient(
    90deg,
    red -200px,
    orange 200px,
    yellow 400px,
    green 600px,
    blue 800px,
    indigo 1000px,
    violet 1200px
  );
}
```

<Figures figure="9-69">Gradient clipping when color stops have negative positions</Figures>

As for percentages, they’re calculated with respect to the total length of the gradient line. A color stop at `50%` will be at the midpoint of the gradient line. Let’s return to our rainbow example, and instead of having a color stop every 25 pixels, we’ll have one every 10% of the gradient line’s length. This would look like the following, which has the result shown in Figure 9-70:

> 至于百分比，是根据梯度线的总长度计算的。在“50%”处的颜色停止点位于渐变线的中点。让我们回到彩虹的例子，不是每 25 个像素有一个颜色停止，我们将有一个每 10%的梯度线的长度。其结果如图 9-70 所示:

```css
#spectrum {
  background-image: linear-gradient(
    90deg,
    red,
    orange 10%,
    yellow 20%,
    green 30%,
    blue 40%,
    indigo 50%,
    violet 60%
  );
}
```

<Figures figure="9-70">Placing color stops every 10 percent</Figures>

As we saw previously, since the last color stop comes before the end of the gradient line, its color (`violet`) is carried through to the end of the gradient. These stops are a bit more spread out than the 25-pixel example we saw earlier, but otherwise things happen in more or less the same way.

> 正如我们前面看到的，由于最后一个颜色停止在渐变线的末端之前，它的颜色(“violet”)被带到渐变的末端。这些定位点比我们之前看到的 25 像素的例子要分散一些，但是其他情况下，事情发生的方式或多或少是相同的。

In cases where some color stops have position values and others don’t, the stops without positions are evenly distributed between the ones that do. Consider the following:

> 在有些颜色停止点有位置值而有些没有的情况下，没有位置的停止点均匀地分布在有位置的停止点之间。考虑以下:

```css
#spectrum {
  background-image: linear-gradient(
    90deg,
    red,
    orange,
    yellow 50%,
    green,
    blue,
    indigo 95%,
    violet
  );
}
```

Because `red` and `violet` don’t have specified position values, they’re taken to be `0%` and `100%`, respectively. This means than `orange`, `green`, and `blue` will be evenly distributed between the explicitly defined positions to either side.

> 因为' red '和' violet '没有指定的位置值，所以它们分别被视为' 0% '和' 100% '。这意味着“橙色”、“绿色”和“蓝色”将均匀地分布在两边明确定义的位置上。

For `orange`, that means the point midway between `red 0%` and `yellow 50%`, which is 25%. For `green` and `blue`, these need to be arranged between `yellow 50%` and `indigo 95%`. That’s a 45% difference, which is divided in three, because there are three intevals between the four values. That means 65% and 80%. In the end, we get the distorted rainbow shown in Figure 9-71, exactly as if we’d declared the following:

> 对于“orange”，它的意思是介于“red 0%”和“yellow 50%”之间的点，后者是 25%。对于“绿色”和“蓝色”，这些需要安排在“黄色 50%”和“靛蓝色 95%”之间。45%的差值，除以 3，因为 4 个值之间有 3 个整数。也就是 65%和 80%最后，我们得到了如图 9-71 所示的扭曲彩虹，就像我们声明了以下内容一样:

```css
#spectrum {
  background-image: linear-gradient(
    90deg,
    red 0%,
    orange 25%,
    yellow 50%,
    green 65%,
    blue 80%,
    indigo 95%,
    violet 100%
  );
}
```

<Figures figure="9-71">Distributing color stops between explicitly placed stops</Figures>

This is the same mechanism used to evenly distribute stops along the gradient line when none of them are given a position. If none of the color stops have been positioned, the first is assumed to be `0%`, the last is assumed to be `100%`, and the other color stops are evenly distributed between those two points.

> 这是相同的机制，用来均匀分布沿梯度线停止时，没有一个给一个位置。如果没有一个颜色停止被定位，第一个被假定为' 0% '，最后一个被假定为' 100% '，另外一个颜色停止被均匀地分布在这两个点之间。

You might wonder what happens if you put two color stops at exactly the same point, like this:

> 你可能想知道如果你把两种颜色停在同一点会发生什么，就像这样:

```css
#spectrum {
  background-image: linear-gradient(
    90deg,
    red 0%,
    orange,
    yellow,
    green 50%,
    blue 50%,
    indigo,
    violet
  );
}
```

All that happens is that the two color stops are put on top of each other. The result is shown in Figure 9-72.

> 所发生的就是这两个色位被叠加在一起。结果如图 9-72 所示。

<Figures figure="9-72">The effect of coincident color stops</Figures>

The gradient blended as usual all along the gradient line, but at the 50% point, it instantly blended from green to blue over zero length. So the gradient blended from yellow at the 33.3% point (two-thirds of the way from 0% to 50%) to green at the 50% point, then blended from green to blue over zero length, then blended from blue at 50% over to indigo at 75% (midway between 50% and 100%).

> 梯度像往常一样沿着梯度线混合，但在 50%的点，它立即从绿色到蓝色的零长度混合。因此，梯度从 33.3%处的黄色(从 0%到 50%的三分之二)混合到 50%处的绿色，然后从绿色到蓝色的零长度混合，然后从 50%处的蓝色到 75%的靛蓝色混合(介于 50%和 100%之间)。

This “hard-stop” effect can be useful if you want to create a striped effect, like that shown in Figure 9-73, which is the result of the following code:

> 如果您想要创建一个条带效果，如图 9-73 所示，这是以下代码的结果，那么这种“硬停止”效果会很有用:

```css
.stripes {
  background-image: linear-gradient(
    90deg,
    gray 0%,
    gray 25%,
    transparent 25%,
    transparent 50%,
    gray 50%,
    gray 75%,
    transparent 75%,
    transparent 100%
  );
}
```

<Figures figure="9-73">Hard-stop stripes</Figures>

OK, so that’s what happens if you put color stops right on top of each other, but what happens if you put one `before` another? Something like this, say:

> 好了，这就是如果你把颜色块放在另一个的上面会发生什么，但是如果你把一个放在另一个的前面会发生什么呢?比如说:

```css
#spectrum {
  background-image: linear-gradient(
    90deg,
    red 0%,
    orange,
    yellow,
    green 50%,
    blue 40%,
    indigo,
    violet
  );
}
```

In that case, the offending color stop (`blue` in this case) is set to the largest specified value of a preceding color stop. Here, it would be set to `50%`, since the stop before it had that position. Thus, the effect is the same as we saw earlier in this section, when the green and blue color stops were placed on top of each other.

> 在这种情况下，违规的颜色停止(在本例中为“蓝色”)被设置为前一个颜色停止的最大指定值。在这里，它将被设置为“50%”，因为在它之前的停止有那个位置。因此，这种效果与我们在本节前面看到的效果相同，即绿色和蓝色停止在彼此的顶部。

The key point here is that the color stop is set to the largest `specified` position of the stop that precedes it. Thus, given the following, the `indigo` color stop would be set to `50%`:

> 这里的关键是颜色停止被设置为它前面的停止的最大的“指定”位置。因此，在以下情况下，'靛'色停止将设置为' 50% ':

```css
#spectrum {
  background-image: linear-gradient(
    90deg,
    red 0%,
    orange,
    yellow 50%,
    green,
    blue,
    indigo 33%,
    violet
  );
}
```

In this case, the largest specified position before the indigo stop is the `50%` specified at the yellow stop. Thus, the gradient fades from red to orange to yellow, then has a hard switch to indigo before fading from indigo to violet. The gradient’s fades from yellow to green to blue to indigo all take place over zero distance. See Figure 9-74 for the results.

> 在本例中，indigo 停止之前的最大指定位置是在黄色停止处指定的“50%”。因此，渐变从红色到橙色到黄色，然后在从靛蓝色到紫罗兰色之前，有一个到靛蓝色的硬开关。渐变从黄色到绿色，从蓝色到靛蓝色的渐变都是在零距离范围内进行的。结果见图 9-74。

<Figures figure="9-74">Handling color stops that are out of place</Figures>

This behavior is the reason why mixing units within a single gradient is generally discouraged. If you mix rems and percentages, for example, you could end up with a situation where a color stop positioned with percentages might end up before an earlier color stop positioned with rems.

> 这就是为什么通常不鼓励在单一梯度内混合单元的原因。例如，如果你将 rems 和百分数混合使用，你可能会遇到这样的情况:一个用百分数定位的颜色停止可能会先于一个用 rems 定位的颜色停止。

#### Setting color hints

Thus far, we’ve worked with color stops, but you may remember that the syntax for linear gradients permits “color hints” after each color stop:

> 到目前为止，我们已经处理了颜色停止，但你可能记得，线性梯度语法允许“颜色提示”后，每个颜色停止:

```css
linear-gradient(
 [[ <angle> | to <side-or-quadrant> ],]? [ <color-stop> [, <color-hint>]? ]# ,
 <color-stop>
)
```

A `<color-hint>` is a way of modifying the blend between the two color stops to either side. By default, the blend from one color stop to the next is linear. Thus, given the following, we get the result shown in Figure 9-75:

> `<color-hint>` 是一种修改两个颜色之间的混合的方法。默认情况下，从一个颜色到下一个颜色的渐变是线性的。因此，给定以下条件，得到如图 9-75 所示的结果:

```css
linear-gradient(
to right, #000 25%, rgb(90%,90%,90%) 75%
)
```

<Figures figure="9-75">Linear blending from one color stop to the next</Figures>

The blend from the 25% point to the 75% point is a constant linear progression from black (`#000`) to a light gray (`rgb(90%,90%,90%)`). Halfway between them, at the 50% mark, the shade of gray is exactly halfway between the colors defined by the color stops to either side. That calculates to `rgb(45%,45%,45%)`.

> 从 25%点到 75%点的混合是从黑色(“#000”)到浅灰色(“rgb(90%，90%，90%)”)的一个恒定的线性级数。在它们的中间，在 50%的标记处，灰色的阴影正好是由颜色停止在任何一边所定义的颜色的中间。计算结果为“rgb(45%，45%，45%)”。

With color hints, we can change the midpoint of the progression. Instead of reaching `rgb(45%,45%,45%)` at the halfway point, it can be set for any point in between the two stops. Thus, the following CSS leads to the result seen in Figure 9-76:

> 通过颜色提示，我们可以改变进程的中点。不是在中途达到“rgb(45%，45%，45%)”，它可以设置为两个站点之间的任何点。因此，下面的 CSS 可以得到如图 9-76 所示的结果:

```css
#ex01 {
  background: linear-gradient(to right, #000 25%, rgb(90%, 90%, 90%) 75%);
}
#ex02 {
  background: linear-gradient(to right, #000 25%, 33%, rgb(90%, 90%, 90%) 75%);
}
#ex03 {
  background: linear-gradient(to right, #000 25%, 67%, rgb(90%, 90%, 90%) 75%);
}
#ex04 {
  background: linear-gradient(to right, #000 25%, 25%, rgb(90%, 90%, 90%) 75%);
}
#ex05 {
  background: linear-gradient(to right, #000 25%, 75%, rgb(90%, 90%, 90%) 75%);
}
```

<Figures figure="9-76">Black-to-gray with differing midpoint hints</Figures>

In the first case (`#ex01`), the default linear progression is used, with the middle color (45% black) occurring at the midpoint between the two color stops.

> 在第一种情况下(' #ex01 ')，使用默认的线性级数，中间颜色(45%黑色)出现在两个颜色停止点之间的中点。

In the second case (`#ex02`), the middle color happens at the 33% point of the gradient line. So the first color stop is at the 25% point on the line, the middle color happens at 33%, and the second color stop happens at 75%.

> 在第二种情况下(' #ex02 ')，中间颜色发生在梯度线的 33%处。所以第一个颜色停止在这条线上的 25%处，中间的颜色在 33%处，第二个颜色停止在 75%处。

In the third example (`#ex03`), the midpoint is at the 67% point of the gradient line; thus, the color fades from black at 25% to the middle color at 67%, and then from that middle color at 67% to light gray at 75%.

> 在第三个例子(' #ex03 ')中，中点位于梯度线的 67%处;因此，颜色从 25%的黑色渐变为 67%的中间色，然后从 67%的中间色渐变为 75%的浅灰色。

The fourth and fifth examples show what happens when you put a color hint’s distance right on top of one of the color stops: you get a “hard stop.”

> 第四个和第五个例子展示了当你把颜色提示的距离放在一个颜色停止点的正上方时会发生什么:你会得到一个“硬停止”。

The interesting thing about color hinting is that the progression from color stop to color hint to color stop is not just a set of two linear progressions. Instead, there is some “curving” to the progression, in order to ease from one side of the color hint to the other. This is easiest to see by comparing what would seem to be, but actually are not, two gradients that do the same thing. As you can see in Figure 9-77, the result is rather different:

> 关于颜色暗示，有趣的是，从颜色停止到颜色提示再到颜色停止的过程并不仅仅是两个线性的过程。相反，有一些“曲线”的进展，以减轻从一边的颜色提示到另一边。这是最容易看到的，通过比较什么似乎是，但实际上不是，两个梯度做相同的事情。正如你在图 9-77 中看到的，结果是相当不同的:

```css
#ex01 {
  background: linear-gradient(
    to right,
    #000 25%,
    rgb(45%, 45%, 45%) 67%,
    /* this is a color stop */ rgb(90%, 90%, 90%) 75%
  );
}
#ex02 {
  background: linear-gradient(
    to right,
    #000 25%,
    67%,
    /* this is a color hint */ rgb(90%, 90%, 90%) 75%
  );
}
```

<Figures figure="9-77">Comparing two linear gradients to one hinted transition</Figures>

Notice how the gray progression is different between the two examples. The first shows a linear progression from black to `rgb(45%,45%,45%)`, and then another linear progression from there to `rgb(90%,90%,90%)`. The second progresses from black to the light gray over the same distance, and the color-hint point is at the 67% mark, but the gradient is altered to attempt a smoother overall progression. The colors at 25%, 67%, and 75% are the same in both examples, but all the other shades along the way are different between the two.

> 注意这两个例子之间的灰度级数是如何不同的。第一个显示从黑色到“rgb(45%，45%，45%)”的线性进展，然后另一个线性进展从那里到“rgb(90%，90%，90%)”。在相同的距离内，第二次从黑色进展到浅灰色，颜色提示点在 67%处，但是渐变被改变以尝试更平滑的整体进展。在这两个示例中，25%、67%和 75%的颜色是相同的，但是这两个示例中的所有其他色调都不同。

<Tips tips="orange">If you’re familiar with animations, you might think to put easing functions (such as <code>ease-in</code>) into a color hint, in order to exert more control over how the colors are blended. This isn’t possible as of late 2017, but the capability was under discussion.</Tips>

#### Gradient lines: the gory details

Now that you have a grasp of the basics of placing color stops, it’s time to look closely at how gradient lines are actually constructed, and thus how they create the effects that they do.

> 现在您已经掌握了放置颜色停止点的基础知识，接下来我们将深入了解渐变线是如何构造的，以及它们是如何产生这样的效果的。

First, let’s set up a simple gradient so we can then dissect how it works:

> 首先，让我们建立一个简单的梯度，这样我们可以剖析它是如何工作的:

```css
linear-gradient(
 55deg, #4097FF, #FFBE00, #4097FF
)
```

Now, how does this one-dimensional construct—a line at 55 degrees on the compass—create a two-dimensional gradient fill? First, the gradient line is placed and its start and ending points determined. This is diagrammed in Figure 9-78, with the final gradient shown next to it.

> 现在，这个一维的结构——在圆规上 55 度的直线——如何创建一个二维的渐变填充?首先，放置梯度线并确定其起点和终点。这是在图 9-78 中显示的，它旁边显示了最终的渐变。

<Figures figure="9-78">The placement and sizing of the gradient line</Figures>

The first thing to make very clear is that the box seen here is not an element—it’s the linear-gradient image itself. (Remember, we’re creating images here.) The size and shape of that image can depend on a lot of things, whether it’s the size of the element’s background or the application of properties like `background-size`, which is a topic we’ll cover in a bit. For now, we’re just concentrating on the image itself.

> 首先要明确的是，这里看到的方框不是一个元素——它是线性渐变图像本身。(记住，我们在这里创建图像。)图像的大小和形状取决于很多东西，无论是元素背景的大小还是“background-size”等属性的应用，这是我们将会讨论的一个主题。现在，我们只关注图像本身。

OK, so in Figure 9-78, you can see that the gradient line goes straight through the center of the image. The gradient line `always` goes through the center of the gradient image. In this case, we set it to a 55-degree angle, so it’s pointing at 55 degrees on the compass. What’s interesting are the start and ending points of the gradient line, which are actually outside the image.

> 好的，在图 9-78 中，你可以看到梯度线直接穿过图像的中心。渐变线“总是”通过渐变图像的中心。在这个例子中，我们设它的角度是 55 度，所以它指向罗盘上的 55 度。有趣的是梯度线的起点和终点，它们实际上在图像外面。

Let’s talk about the start point first. It’s the point on the gradient line where a line perpendicular to the gradient line intersects with the corner of the image furthest away from the gradient line’s direction (`55deg`). Conversely, the gradient line’s ending point is the point on the gradient line where a perpendicular line intersects the corner of the image nearest to the gradient line’s direction.

> 我们先来谈谈起点。它是梯度线上的一个点，在这个点上，一条垂直于梯度线的线与距离梯度线方向最远的图像角相交(' 55deg ')。反之，梯度线的终点是梯度线上的点，在该点上，一条垂线与图像中最接近梯度线方向的角相交。

Bear in mind that the terms “start point” and “ending point” are a little bit misleading—the gradient line doesn’t actually stop at either point. The gradient line is, in fact, infinite. However, the start point is where the first color stop will be placed by default, as it corresponds to position value `0%`. Similarly, the ending point corresponds to the position value `100%`.

> 请记住，“起点”和“终点”这两个术语有点误导人——梯度线实际上并不在这两个点上停止。梯度线实际上是无限的。但是，默认情况下，起始点是第一个颜色停止的位置，因为它对应于位置值“0%”。类似地，结束点对应于位置值“100%”。

Therefore, given the gradient we defined before:

> 因此，给定我们之前定义的梯度:

```css
linear-gradient(
 55deg, #4097FF, #FFBE00, #4097FF
)
```

the color at the start point will be `#4097FF`, the color at the midpoint (which is also the center of the image) will be `#FFBE00`, and the color at the ending point will be `#4097FF`, with smooth blending in between. This is illustrated in Figure 9-79.

> 起始点的颜色为“#4097FF”，中点(也就是图像的中心)的颜色为“#FFBE00”，结束点的颜色为“#4097FF”，中间平滑混合。如图 9-79 所示。

<Figures figure="9-79">The calculation of color along the gradient line</Figures>

All right, fine so far. But, you may wonder, how do the bottom-left and top-right corners of the image get set to the same blue that’s calculated for the start and ending points, if those points are outside the image? Because the color at each point along the gradient line is extended out perpendicularly from the gradient line. This is partially shown in Figure 9-80 by extending perpendicular lines at the start and ending points, as well as every 5% of the gradient line between them.

> 到目前为止还好。但是，您可能想知道，如果图像的左下角和右上角位于图像外部，那么如何将它们设置为与计算起点和终点的蓝色相同的蓝色呢?因为梯度线上每一点的颜色都是从梯度线上垂直延伸出来的。在图 9-80 中，通过延伸起点和终点的垂线，以及它们之间的梯度线的每 5%，可以部分地看到这一点。

<Figures figure="9-80">The extension of selected colors along the gradient line</Figures>

That should be enough to let you fill in the rest mentally, so let’s consider what happens to the gradient image in various other settings. We’ll use the same gradient definition as before, but this time apply it to wide, square, and tall images. These are shown in Figure 9-81. Note how the start-point and ending-point colors always make their way into the corners of the gradient image.

> 这应该足够让您在思想上填充剩下的部分，所以让我们考虑一下在其他各种设置中渐变图像会发生什么。我们将使用与之前相同的渐变定义，但这次将其应用于宽、方和高的图像。如图 9-81 所示。请注意起始点和结束点的颜色是如何进入渐变图像的各个角落的。

<Figures figure="9-81">How gradients are constructed for various images</Figures>

Note how I very carefully said “the start-point and ending-point colors,” and did `not` say “the start and end colors.” That’s because, as we saw earlier, color stops can be placed before the start point and after the ending point, like so:

> 注意我是如何非常小心地说“起点和终点的颜色”，而不是“开始和结束的颜色”。“这是因为，正如我们之前看到的，颜色停止可以放在开始点之前和结束点之后，就像这样:

```css
linear-gradient(
 55deg, #4097FF -25%, #FFBE00, #4097FF 125%
)
```

The placement of these color stops as well as the start point and ending point, the way the colors are calculated along the gradient line, and the final gradient are all shown in Figure 9-82.

> 这些颜色停止点的位置以及开始点和结束点，颜色沿着梯度线计算的方式，以及最终的梯度都显示在图 9-82 中。

<Figures figure="9-82">A gradient with stops beyond the start and ending points</Figures>

Once again, we see that the colors in the bottom-left and top-right corners match the start-point and ending-point colors. It’s just that in this case, since the first color stop came before the start point, the actual color at the start point is a blend of the first and second color stops. Likewise for the ending point, which is a blend of the second and third color stops.

> 我们再次看到，左下角和右上角的颜色与起始点和结束点的颜色匹配。只是在这种情况下，因为第一个颜色停止在开始点之前，开始点的实际颜色是第一个和第二个颜色停止的混合。同样的，结束点是第二和第三种颜色的混合。

Now here’s where things get a little bit wacky. Remember how you can use directional keywords, like `top` and `right`, to indicate the direction of the gradient line? Suppose you wanted the gradient line to go toward the top right, so you create a gradient image like this:

> 这就是事情变得有点古怪的地方。还记得如何使用方向关键字(如“top”和“right”)来指示渐变线的方向吗?假设你想让渐变线指向右上角，所以你创建了一个这样的渐变图像:

```css
linear-gradient(
 to top right, #4097FF -25%, #FFBE00, #4097FF 125%
)
```

This does `not` cause the gradient line to intersect with the top-right corner. Would that it did! Instead, what happens is a good deal stranger. First, let’s diagram it in Figure 9-83 so that we have something to refer to.

> 这不会导致梯度线与右上角相交。但愿如此!相反，所发生的是一个非常奇怪的事情。首先，让我们在图 9-83 中对它进行图解，以便我们可以参考一些东西。

Your eyes do not deceive you: the gradient line is way off from the top-right corner. On the other hand, it `is` headed into the top-right quadrant of the image. That’s what to top right really means: head into the top-right quadrant of the image, not into the top-right corner.

> 你的眼睛不会欺骗你:梯度线离右上角很远。另一方面，它“是”朝向图像的右上角象限。这就是右上角的真正含义:进入图像的右上角象限，而不是右上角。

As Figure 9-83 shows, the way to find out exactly what that means is to do the following:

> 如图 9-83 所示，要准确地找出这意味着什么，可以执行以下操作:

1. Shoot a line from the midpoint of the image into the corners adjacent to the corner in the quadrant that’s been declared. Thus, for the top-right quadrant, the adjacent corners are the top left and bottom right.
2. Draw the gradient line perpendicular to that line, pointing into the declared quadrant.
3. Construct the gradient—that is, determine the start and ending points, place or distribute the color stops, then calculate the entire gradient image, as per usual.

---

> 1. 从图像的中点到已经声明的象限中与角落相邻的角落处画一条线。因此，对于右上象限，相邻的角是左上和右下。
> 2. 画出垂直于这条线的梯度线，指向指定的象限。
> 3. 构造梯度——即确定起始点和结束点，放置或分布颜色停止点，然后像往常一样计算整个梯度图像。

<Figures figure="9-83">A gradient headed toward the top right</Figures>

This process has a few interesting side effects. First, it means that the color at the midpoint will always stretch from one quadrant-adjacent corner to the other. Second, it means that if the image’s shape changes—that is, if its ratio of height to width changes—then the gradient line will also change direction, meaning that the gradient will reorient. So watch out for that if you have flexible elements. Third, a perfectly square gradient image will have a gradient line that intersects with a corner. Examples of these three side effects are depicted in Figure 9-84, using the following gradient definition in all three cases:

> 这个过程有一些有趣的副作用。首先，它意味着中点的颜色总是从相邻的一个象限角延伸到另一个象限角。第二，它意味着如果图像的形状改变了，也就是说，如果它的高宽比改变了，那么梯度线也会改变方向，这意味着梯度线将重新定向。所以如果你有灵活的元素，就要小心了。第三，一个完全平方的梯度图像将有一个与一个角相交的梯度线。图 9-84 描述了这三种副作用的例子，在所有三种情况下都使用了下面的梯度定义:

```css
linear-gradient(
 to top right, purple, green 49.5%, black 50%, green 50.5%, gold
)

```

<Figures figure="9-84">Examples of the side effects of a quadrant-directed gradient</Figures>

Sadly, there is no way to say “point the gradient line into the corner of a nonsquare image” short of calculating the necessary degree heading yourself and declaring it explicitly, a process that will require JavaScript unless you know the image will always be an exact size in all cases, forever.

> 可悲的是,没有办法说“点渐变线的角落 nonsquare 形象”的计算必要的程度向自己和显式地声明,这一过程将需要 JavaScript 除非你知道形象将永远是一个确切的大小在所有情况下,直到永远。

### 9.3.2 Radial Gradients

Linear gradients are pretty awesome, but there are times when you really want a circular gradient. You can use such a gradient to create a spotlight effect, a circular shadow, a rounded glow, or any number of other effects. The syntax used is similar to that for linear gradients, but there are some interesting differences:

> 线性梯度是非常棒的，但有时你真的想要一个圆形梯度。你可以使用这样的渐变来创建一个聚光灯效果，一个圆形阴影，一个圆形辉光，或任何其他效果。使用的语法类似于线性梯度，但有一些有趣的区别:

```css
radial-gradient(
 [ [ <shape> ‖ <size> ] [ at <position>]? , | at <position>, ]?
 [ <color-stop> [, <color-hint>]? ] [, <color-stop> ]+
)
```

What this boils down to is you can optionally declare a shape and size, optionally declare where it center of the gradient is positioned, and then declare two or more color stops with optional color hints in between the stops. There are some interesting options in the shape and size bits, so let’s build up to those.

> 归根到底，你可以选择声明一个形状和大小，可以选择声明渐变的中心位置，然后声明两个或多个颜色停止，在停止之间有可选的颜色提示。在形状和大小方面有一些有趣的选项，所以让我们来构建这些选项。

First, let’s look at a simple radial gradient—the simplest possible, in fact—presented in a variety of differently shaped elements (Figure 9-85):

> 首先，让我们来看看一个简单的径向梯度——实际上是最简单的，以各种不同形状的元素表示的(图 9-85):

```css
.radial {
  background-image: radial-gradient(purple, gold);
}
```

<Figures figure="9-85">A simple radial gradient in multiple settings</Figures>

In all of these cases, because no position was declared, the default of `center` was used. Because no shape was declared, the shape is an ellipse for all cases but the square element; in that case, the shape is a circle. Finally, because no color-stop or color-hint positions were declared, the first is placed at the beginning of the gradient ray, and the last at the end, with a linear blend from one to the other.

> 在所有这些情况下，因为没有声明位置，所以使用默认的' center '。因为没有声明形状，所以除了 square 元素外，所有情况下形状都是椭圆;在这种情况下，形状就是一个圆。最后，因为没有颜色停止或颜色提示位置被声明，第一个被放置在渐变射线的开始，最后一个被放置在末尾，从一个到另一个的线性混合。

That’s right: the gradient ray, which is the radial equivalent to the gradient line in linear gradients. It extends outward from the center of the gradient directly to the right, and the rest of the gradient is constructed from it. (We’ll get to the details on that in just a bit.)

> 这是对的，梯度射线，它在径向上等价于线性梯度中的梯度线。它从梯度的中心直接向右延伸，其余的梯度是由它构成的。(我们稍后会详细讨论这一点。)

#### Shape and size

First off, there are exactly two possible shape values (and thus two possible shapes) for a radial gradient: `circle` and `ellipse`. The shape of a gradient can be declared explicitly, or it can be implied by the way you size the gradient image.

> 首先，径向渐变有两个可能的形状值(因此也有两个可能的形状):“圆”和“椭圆”。渐变的形状可以显式地声明，也可以通过设置渐变图像的大小来暗示。

So, on to sizing. As always, the simplest way to size a radial gradient is with either one non-negative length (if you’re sizing a circle) or two non-negative lengths (if it’s an ellipse). Say you have this radial gradient:

> 那么，关于尺寸。通常，确定径向梯度最简单的方法是使用一个非负长度(如果要调整圆的大小)或两个非负长度(如果是椭圆)。假设你有这个径向梯度:

```css
radial-gradient(50px, purple, gold)
```

This creates a circular radial gradient that fades from purple at the center to gold at a distance of 50 pixels from the center. If we add another length, then the shape becomes an ellipse that’s as wide as the first length, and as tall as the second length:

> 这样就创建了一个圆形的径向渐变，从中心的紫色渐变到中心 50 像素处的金色渐变。如果我们添加另一个长度，那么形状就变成了一个与第一个长度一样宽，与第二个长度一样高的椭圆:

```css
radial-gradient(50px 100px, purple, gold)
```

These two gradients are illustrated in Figure 9-86.

> 这两个梯度如图 9-86 所示。

<Figures figure="9-86">Simple radial gradients</Figures>

Notice how the shape of the gradients has nothing to do with the overall size and shape of the images in which they appear. If you make a gradient a circle, it will be a circle, even if it’s inside a rectangular gradient image. So too will an ellipse always be an ellipse, even when inside a square gradient image (where it will look like a circle, since an ellipse with the same height and width forms a circle).

> 请注意，渐变的形状与图像的整体大小和形状没有任何关系。如果你把渐变做成一个圆，它就是一个圆，即使它是在一个矩形渐变图像中。一个椭圆也总是一个椭圆，即使在一个正方形渐变图像中(在这里它看起来像一个圆，因为一个具有相同高度和宽度的椭圆形成一个圆)。

You can also use percentage values for the size, but `only` for ellipses. Circles cannot be given percentage sizes because there’s no way to indicate the axis to which that percentage refers. (Imagine an image 100 pixels tall by 500 wide. Should `10%` mean 10 pixels or 50 pixels?) If you try to provide percentage values for a circle, the entire declaration will fail due to the invalid value.

> 您也可以使用百分比值的大小，但'只'的省略号。圆圈不能给出百分比大小，因为无法指出百分比所指向的轴。(想象一幅 100 像素高、500 像素宽的图像。“10%”是指 10 个像素还是 50 个像素?)如果您试图为一个圆圈提供百分比值，则整个声明将由于无效值而失败。

If you do supply percentages to an ellipse, then as usual, the first refers to the horizontal axis and the second to the vertical. The following gradient is shown in various settings in Figure 9-87:

> 如果您确实向椭圆提供百分比，那么与往常一样，第一个表示水平轴，第二个表示垂直轴。如下图 9-87 所示:

```css
radial-gradient(50% 25%, purple, gold)
```

<Figures figure="9-87">Percentage-sized elliptical gradients</Figures>

When it comes to ellipses, you’re also able to mix lengths and percentages, with the usual caveat to be careful. So if you’re feeling confident, you can absolutely make an elliptical radial gradient 10 pixels tall and half the element width, like so:

> 当涉及到省略号时，您还可以混合使用长度和百分比，但要注意通常的警告。因此，如果你感觉自信，你绝对可以使椭圆径向梯度 10 像素高和一半的元素宽度，像这样:

```css
radial-gradient(50% 10px, purple, gold)
```

As it happens, lengths and percentages aren’t the only way to size radial gradients. In addition to those value types, there are also four keywords available for sizing radial gradients, the effects of which are summarized in Table 9-3.

> 实际上，长度和百分比并不是确定径向梯度大小的惟一方法。除了这些值类型之外，还有四个关键字可以用来调整径向梯度的大小，其效果如表 9-3 所示。

| Keyword                   | Meaning                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| closest-side              | If the radial gradient’s shape is a circle, the gradient is sized so that the end of the gradient ray exactly touches the edge of the gradient image that is closest to the center point of the radial gradient. If the shape is an ellipse, then the end of the gradient ray exactly touches the closest edge in each of the horizontal and vertical axes.                                                                                                                                                                                           |
| farthest-side             | If the radial gradient’s shape is a circle, the gradient is sized so that the end of the gradient ray exactly touches the edge of the gradient image that is farthest from the center point of the radial gradient. If the shape is an ellipse, then the end of the gradient ray exactly touches the farthest edge in each of the horizontal and vertical axes.                                                                                                                                                                                       |
| closest-corner            | If the radial gradient’s shape is a circle, the gradient is sized so that the end of the gradient ray exactly touches the corner of the gradient image that is closest to the center point of the radial gradient. If the shape is an ellipse, then the end of the gradient ray still touches the corner closest to the center, and the ellipse has the same aspect ratio that it would have had if closest-side had been specified.                                                                                                                  |
| farthest-corner (default) | If the radial gradient’s shape is a circle, the gradient is sized so that the end of the gradient ray exactly touches the corner of the gradient image that is farthest from the center point of the radial gradient. If the shape is an ellipse, then the end of the gradient ray still touches the corner farthest from the center, and the ellipse has the same aspect ratio that it would have had if farthest-side had been specified. Note: this is the default size value for a radial gradient and so is used if no size values are declared. |

In order to better visualize the results of each keyword, see Figure 9-88, which depicts each keyword applied as both a circle and an ellipse.

> 为了更好地可视化每个关键字的结果，请参见图 9-88，图中将每个关键字描述为一个圆和一个椭圆。

<Figures figure="9-88">The effects of radial gradient sizing keywords</Figures>

These keywords cannot be mixed with lengths or percentages in elliptical radial gradients; thus, closest-side 25px is invalid and will be ignored.

> 这些关键字不能与长度或百分比混合在椭圆径向梯度;因此，关闭端 25px 是无效的，将被忽略。

Something you might have noticed in Figure 9-88 is that the gradients didn’t start at the center of the image. That’s because they were positioned elsewhere, which is the topic of the next section.

> 在图 9-88 中，您可能已经注意到渐变并不是从图像中心开始的。这是因为它们被放置在其他地方，这是下一节的主题。

#### Positioning radial gradients

If you want to shift the center of a radial gradient away from the default of `center`, then you can do so using any position value that would be valid for `background-position`. I’m not going to reproduce that rather complicated syntax here; flip back to the section on `background-position` (“Background Positioning” on page 404) if you need a refresher.

> 如果你想把径向渐变的中心从默认的“中心”移开，那么你可以使用任何对“背景-位置”有效的位置值。我不打算在这里重复这个复杂的语法;如果你需要复习，请翻回“背景-位置”一节(“背景定位”在 404 页)。

When I say “any position value that would be valid,” that means any permitted combination of lengths, percentages, keywords, and so on. It also means that if you leave off one of the two position values, it will be inferred just the same as for `background-position`. So, just for one example, `center` is equivalent to `center center`. The one major difference between radial gradient positions and background positions is the default: for radial gradients, the default position is `center`, not `0% 0%`.

> 当我说“任何有效的位置值”时，这意味着任何允许的长度、百分比、关键字等组合。它还意味着，如果您省略了两个位置值中的一个，那么它将与“background-position”一样被推断出来。举个例子，center 和 center 是等价的。径向梯度位置和背景位置的一个主要区别是默认:对于径向梯度，默认位置是“中心”，而不是“0% 0%”。

To give some idea of the possibilities, consider the following rules, illustrated in Figure 9-89:

> 为了给出一些可能性的概念，请考虑以下规则，如图 9-89 所示:

```css
radial-gradient(at bottom left, purple, gold);
radial-gradient(at center right, purple, gold);
radial-gradient(at 30px 30px, purple, gold);
radial-gradient(at 25% 66%, purple, gold);
radial-gradient(at 30px 66%, purple, gold);
```

<Figures figure="9-89">Changing the center position of radial gradients</Figures>

None of those positioned radial gradients were explicitly sized, so they all defaulted to `farthest-corner`. That’s a reasonable guess at the intended default behavior, but it’s not the only possibility. Let’s mix some sizes into the gradients we just saw and find out how that changes things (as depicted in Figure 9-90):

> 这些定位径向梯度没有明确的大小，所以他们都默认为“最远的角落”。这是对预期的默认行为的合理猜测，但这不是唯一的可能性。让我们混合一些大小到梯度，我们刚刚看到，并找出如何改变事情(如图 9-90 所示):

```css
radial-gradient(30px at bottom left, purple, gold);
radial-gradient(30px 15px at center right, purple, gold);
radial-gradient(50% 15% at 30px 30px, purple, gold);
radial-gradient(farthest-side at 25% 66%, purple, gold);
radial-gradient(farthest-corner at 30px 66%, purple, gold);
```

<Figures figure="9-90">Changing the center position of explicitly sized radial gradients</Figures>

Nifty. Now, suppose we want something a little more complicated than a fade from one color to another. Next stop, color stops!

> 漂亮的。现在，假设我们想要一个比从一种颜色到另一种颜色渐变更复杂的东西。下一站，颜色停止!

#### Radial color stops and the gradient ray

Color stops for radial gradients have the same syntax, and work in a similar fashion, to linear gradients. Let’s return to the simplest possible radial gradient and follow it with a more explicit equivalent:

> 径向梯度的颜色停止具有与线性梯度相同的语法和工作方式。让我们回到最简单的径向梯度，并遵循它与一个更显式等价:

```css
radial-gradient(purple, gold);
radial-gradient(purple 0%, gold 100%);
```

So the gradient ray extends out from the center point. At 0% (the start point, and also the center of the gradient), the ray will be purple. At 100% (the ending point), the ray will be gold. Between the two stops is a smooth blend from purple to gold; beyond the ending point, solid gold.

> 所以梯度光线从中心点向外延伸。在 0%处(起始点，也是渐变的中心)，射线将是紫色的。在 100%(终点)处，射线为金色。两站之间是紫色到金色的平滑过渡;在终点之外，是纯金。

If we add a stop between purple and gold, but don’t give it a position, then it will be placed midway between them, and the blending will be altered accordingly, as shown in Figure 9-91:

> 如果我们在紫色和金色之间添加一个 stop，但是不给它一个位置，那么它会被放置在它们之间的中间，然后混合会相应地改变，如图 9-91 所示:

```css
radial-gradient(100px circle at center, purple 0%, green, gold 100%);
```

<Figures figure="9-91">Adding a color stop</Figures>

We’d have gotten the same result if we’d added green 50% there, but you get the idea. The gradient ray’s color goes smoothly from purple to green to gold, and then is solid gold beyond that point on the ray.

> 如果我们在这里加入 50%的绿色，我们会得到相同的结果，但是你明白我的意思。渐变光线的颜色从紫色到绿色再到金色，然后是纯金色。

This illustrates one difference between gradient lines (for linear gradients) and gradient rays: a linear gradient is derived by extending the color at each point along the gradient line off perpendicular to the gradient line. A similar behavior occurs with a radial gradient, except in that case, they aren’t lines that come off the gradient ray. Instead, they are ellipses that are scaled-up or scaled-down versions of the ellipse at the ending point. This is illustrated in Figure 9-92, where an ellipse shows its gradient ray and then the ellipses that are drawn at various points along that ray.

> 这说明了梯度线(对于线性梯度)和梯度射线之间的一个不同之处:线性梯度是通过在与梯度线垂直的梯度线上的每个点上扩展颜色而得到的。类似的行为发生在径向梯度，除了在这种情况下，他们不是线，从梯度射线。相反，它们是在端点处放大或缩小的椭圆。如图 9-92 所示，其中一个椭圆表示它的梯度光线，然后在沿该光线的不同点绘制椭圆。

<Figures figure="9-92">The gradient ray and some of the ellipses it spawns</Figures>

That brings up an interesting question: how is the ending point (the `100%` point, if you like) determined for each gradient ray? It’s the point where the gradient ray intersects with the shape described by the size. In the case of a circle, that’s easy: the gradient ray’s ending point is however far from the center that the size value `indicates`. So for a 25px circle gradient, the ending point of the ray is 25 pixels from the center.

> 这就引出了一个有趣的问题:如何确定每条梯度射线的终点(如果你愿意，可以称之为“100%”点)?它是梯度射线与由大小描述的形状相交的点。对于圆形，这很简单:渐变射线的结束点距离大小值“指示”的中心有多远。对于一个 25px 的圆形渐变，射线的结束点距离中心 25 个像素。

For an ellipse, it’s essentially the same operation, except that the distance from the center is dependent on the horizontal axis of the ellipse. Given a radial gradient that’s a `40px 20px ellipse`, the ending point will be 40 pixels from the center and directly to its right. Figure 9-93 shows this in some detail.

> 对于一个椭圆，它本质上是相同的操作，只是到中心的距离依赖于椭圆的水平轴。如果径向渐变是一个“40px 20px 椭圆”，那么结束点将是距离中心 40 个像素，并直接向右。图 9-93 详细显示了这一点。

<Figures figure="9-93">Setting the gradient ray’s ending point</Figures>

Another difference between linear gradient lines and radial gradient rays is that you can see beyond the ending point. If you recall, a linear gradient line is always drawn so that you can see the colors at the 0% and 100% points, but nothing beyond them; the gradient line can never be any smaller than the longest axis of the gradient image, and will frequently be longer than that. With a radial gradient, on the other hand, you can size the radial shape to be smaller than the total gradient image. In that case, the color at the last color stop is extended outward from the ending point. (We’ve already seen this in several previous figures.)

> 线性梯度线和径向梯度线的另一个区别是，你可以看到终点以外的地方。如果你还记得，一个线性梯度线总是被画出来，所以你可以看到在 0%和 100%点的颜色，但没有超过他们;梯度线永远不可能比梯度图像的最长轴小，而且经常会比最长轴长。在径向梯度，另一方面，你可以大小径向形状小于总梯度图像。在这种情况下，最后一个颜色停止点的颜色从结束点向外延伸。(我们在之前的几幅图中已经看到了这一点。)

Conversely, if you set a color stop that’s beyond the ending point of a ray, you might get to see the color out to that stop. Consider the following gradient, illustrated in Figure 9-94:

> 相反地，如果你设置一个颜色的停止点在射线的结束点之外，你可能会看到颜色在那个停止点之外。考虑下面的梯度，如图 9-94 所示:

```css
radial-gradient(50px circle at center, purple, green, gold 80px)
```

<Figures figure="9-94">Color stops beyond the ending point</Figures>

The first color stop has no position, so it’s set to `0%`, which is the center point. The last color stop is set to `80px`, so it will be 80 pixels away from the center in all directions. The middle color stop, `green`, is placed midway between the two (40 pixels from the center). So we get a gradient that goes out to gold at 80 pixels and then continues gold beyond that point.

> 第一个颜色停止没有位置，所以它被设置为' 0% '，这是中心点。最后一个颜色停止设置为' 80px '，所以它将是 80 像素的中心，在所有方向。中间的颜色停止，“绿色”，被放置在两个中间(距离中心 40 像素)。所以我们得到了一个渐变，在 80 像素处过渡到金色，然后继续过渡到金色。

This happens even though the circle was explicitly set to be 50 pixels large. It still is 50 pixels in radius, it’s just that the positioning of the last color stop makes that fact vaguely irrelevant. Visually, we might as well have declared this:

> 即使圆被显式地设置为 50 像素大，也会发生这种情况。它仍然是 50 像素的半径，只是最后一个颜色停止的定位使这个事实模糊无关。在视觉上，我们不妨这样声明:

```css
radial-gradient(80px circle at center, purple, green, gold)
```

or, more simply, just this:

> 或者，更简单地说，就是这样:

```css
radial-gradient(80px, purple, green, gold)
```

The same behaviors apply if you use percentages for your color stops. These are equivalent to the previous examples, and to each other, visually speaking:

> 同样的行为也适用于你的颜色停止百分比。这些与前面的例子是等价的，并且从视觉上来说，它们之间是相互等价的:

```css
radial-gradient(50px, purple, green, gold 160%)
radial-gradient(80px, purple, green, gold 100%)
```

Now, what if you set a negative position for a color stop? It’s pretty much the same result as we saw with linear gradient lines: the negative color stop is used to figure out the color at the start point, but is otherwise unseen. Thus, the following gradient will have the result shown in Figure 9-95:

> 现在，如果你设置一个颜色停止的负位置呢?这与我们看到的线性梯度线的结果几乎相同:负色停止是用来找出在开始点的颜色，但在其他方面是看不见的。因此，下面的梯度将得到如图 9-95 所示的结果:

```css
radial-gradient(80px, purple -40px, green, gold)
```

<Figures figure="9-95">Handling a negative color-stop position</Figures>

Given these color-stop positions, the first color stop is at `-40px`, the last is at `80px` (because, given its lack of an explicit position, it defaults to the ending point), and the middle is placed midway between them. The result is the same as if we’d explicitly said:

> 考虑到这些颜色停止位置，第一个颜色停止在“-40px”，最后一个颜色停止在“80px”(因为它没有一个明确的位置，它默认是结束点)，中间被放置在它们之间。结果是一样的，如果我们明确地说:

```css
radial-gradient(80px, purple -40px, green 20px, gold 80px)
```

That’s why the color at the center of the gradient is a green-purple: it’s a blend of onethird urple, two-thirds green. From there, it blends the rest of the way to green, and then on to gold. The rest of the purple-green blend, the part that sits on the “negative space” of the gradient ray, is invisible.

> 这就是为什么渐变中心的颜色是绿紫色:它混合了三分之一的 urple，三分之二的 green。从这里开始，它将剩下的部分混合成绿色，然后变成金色。其余的紫绿混合，也就是渐变光线的“负空间”，是不可见的。

#### Degenerate cases

Given that we can declare size and position for a radial gradient, the question arises: what if a circular gradient has zero radius, or an elliptical gradient has zero height or width? These conditions aren’t quite as hard to create as you might think: besides explicitly declaring that a radial gradient has zero size using `0px` or `0%`, you could also do something like this:

> 既然我们可以声明径向渐变的大小和位置，那么问题来了:如果一个圆形渐变的半径为零，或者一个椭圆渐变的高度或宽度为零呢?创建这些条件并不像您想象的那么难:除了使用' 0px '或' 0% '明确声明径向渐变的大小为 0 外，您还可以这样做:

```css
radial-gradient(closest-corner circle at top right, purple, gold)
```

The gradient’s size is set to `closest-corner`, and the center has been moved into the `top` right `corner`, so the closest corner is zero pixels away from the center. Now what?

> 梯度的大小设置为“最接近的角落”，中心已移动到“顶部”右“角落”，所以最近的角落是零像素远离中心。现在怎么办呢?

In this case, the specification very explicitly says that the gradient should be rendered as if it’s “a circle whose radius [is] an arbitrary very small number greater than zero.”

> 在本例中，规范非常明确地指出，应该将梯度呈现为“一个半径[是]任意一个大于零的非常小的数的圆”。

So that might mean as if it had a radius of one-one-billionth of a pixel, or a picometer, or heck, the Planck length. (Kids, ask your science teacher.) The interesting thing is that it means the gradient is still a circle. It’s just a very, very, very small circle. Probably, it will be too small to actually render anything visible. If so, you’ll just get a solidcolor fill that corresponds to the color of the last color stop instead.

> 这可能意味着它的半径是十亿分之一像素，或者一个比例尺，或者普朗克长度。(孩子们，问你们的科学老师。)有趣的是，这意味着梯度仍然是一个圆。它只是一个非常非常小的圆。很可能，它太小了，实际上无法呈现任何可见的东西。如果是这样，您将得到一个 solidcolor 填充，它对应于最后一个颜色停止的颜色。

Ellipses with zero-length dimensions have fascinatingly different defined behaviors. Let’s assume the following:

> 尺寸为零的椭圆具有令人着迷的不同定义行为。让我们假设如下:

```css
radial-gradient(0px 50% at center, purple, gold)
```

The specification states that any ellipse with a zero width is rendered as if it’s “an ellipse whose height [is] an arbitrary very large number and whose width [is] an arbitrary very small number greater than zero.” In other words, render it as though it’s a linear gradient mirrored around the vertical axis running through the center of the ellipse. The specification also says that in such a case, any color stops with percentage positions resolve to `0px`. This will usually result in a solid color matching the color defined for the last color stop.

> 该规范规定，任何宽度为 0 的椭圆都被渲染成“高度为任意一个非常大的数，宽度为任意一个大于 0 的非常小的数的椭圆”。换句话说，渲染它，就好像它是一个线性梯度镜像，围绕着贯穿椭圆中心的垂直轴。该规范还说，在这种情况下，任何颜色的百分比位置停止解析为' 0px '。这通常会导致一个纯色匹配的颜色定义的最后一个颜色停止。

On the other hand, if you use lengths to position the color stops, you can get a vertically mirrored horizontal linear gradient for free. Consider the following gradient, illustrated in Figure 9-96:

> 另一方面，如果你使用长度来定位颜色停止，你可以得到一个垂直镜像水平线性梯度免费。考虑下面的梯度，如图 9-96 所示:

```css
radial-gradient(0px 50% at center, purple 0px, gold 100px)
```

<Figures figure="9-96">The effects of a zero-width ellipse</Figures>

How did this happen? First, remember that the specification says that the `0px horizontal` width is treated as if it’s a tiny non-zero number. For the sake of illustration, let’s suppose that’s one-one-thousandth of a pixel (0.001 px). That means the ellipse shape is a thousandth of a pixel wide by half the height of the image. Again for the sake of illustration, let’s suppose that’s a height of 100 pixels. That means the first ellipse shape is a thousandth of a pixel wide by 100 pixels tall, which is an aspect ratio of 0.001:100, or 1:100,000.

> 这是怎么发生的?首先，请记住，规范中说“0px 水平”宽度被视为一个很小的非零值。为了便于说明，让我们假设这是千分之一像素(0.001 px)。这意味着椭圆形状的像素宽度是图像高度的千分之一。为了便于说明，假设高度为 100 像素。这意味着第一个椭圆形状的像素宽为千分之一，高为 100 像素，长宽比为 0.001:100，即 1:10 万。

OK, so every ellipse drawn along the gradient ray has a 1:100,000 aspect ratio. That means the ellipse at half a pixel along the gradient ray is 1 pixel wide and 100,000 pixels tall. At 1 pixel, it’s 2 pixels wide and 200,000 pixels tall. At 5 pixels, the ellipse is 10 pixels by a million pixels. At 50 pixels along the gradient ray, the ellipse is 100 pixels wide and 10 million tall. And so on. This is diagrammed in Figure 9-97.

> 所以沿梯度线画出的每个椭圆的长宽比都是 1:10 万。这意味着沿梯度光线半像素处的椭圆宽 1 像素，高 100,000 像素。1 像素，2 像素宽，20 万像素高。在 5 像素处，椭圆是 10 像素 ×100 万像素。沿梯度光线 50 像素处，椭圆宽 100 像素，高 1000 万。等等。这是在图 9-97 中绘制的。

<Figures figure="9-97">Very, very tall ellipses</Figures>

So you can see why the visual effect is of a mirrored linear gradient. These ellipses are effectively drawing vertical lines. Technically they aren’t, but in practical terms they are. The result is as if you have a vertically mirrored horizontal gradient, because each ellipse is centered on the center of the gradient, and both sides of it get drawn. While this may be a radial gradient, we can’t see its radial nature.

> 所以你可以看到为什么视觉效果是镜像线性梯度。这些椭圆有效地画出了垂直线。从技术上讲它们不是，但实际上它们是。结果就好像你有一个垂直镜像的水平梯度，因为每个椭圆都以梯度的中心为中心，它的两边都被画出来了。虽然这可能是一个径向梯度，我们不能看到它的径向性质。

On the other hand, if the ellipse has width but not height, the results are quite different. You’d think the result would be to have a vertical linear gradient mirrored around the horizontal axis, but not so! Instead, the result is a solid color equal to the last color stop. (Unless it’s a repeating gradient, a subject we’ll turn to shortly, in which case it should be a solid color equal to the average color of the gradient.) So, given either of the following, you’ll get a solid gold:

> 另一方面，如果椭圆有宽度而没有高度，结果会有很大的不同。你会认为结果会是一个垂直的线性梯度镜像围绕水平轴，但不是这样!相反，结果是一个纯色等于最后一个颜色停止。(除非它是一个重复的渐变，我们很快就会讲到这个主题，在这种情况下，它应该是一个纯色，等于渐变的平均颜色。)所以，如果你选择了以下任何一种，你就会得到一枚纯金:

```css
radial-gradient(50% 0px at center, purple, gold)
radial-gradient(50% 0px at center, purple 0px, gold 100px)
```

Why the difference? It goes back to how radial gradients are constructed from the gradient ray. Again, remember that, per the specification, a zero distance here is treated as a very small non-zero number. As before, we’ll assume that `0px` is reassigned to `0.001px`, and that the `50%` evaluates to 100 pixels. That’s an aspect ratio of 100:0.001, or 100,000:1.

> 为什么会有这样的差异呢?这就回到了如何从梯度射线构造径向梯度。同样，请记住，根据规范，这里的零距离被视为一个非常小的非零数。与前面一样，我们将假定' 0px '被重新分配为' 0.001px '， ' 50% '的计算结果为 100 像素。长宽比是 100:0。001，也就是 10 万:1。

So, to get an ellipse that’s 1 pixel tall, the width of that ellipse must be 100,000 pixels. But our last color stop is only at 100 pixels! At that point, the ellipse that’s drawn is 100 pixels wide and 1,000th of a pixel tall. All of the purple-to-gold transition that happens along the gradient ray has to happen in that thousandth of a pixel. Everything after that is gold, as per the final color stop. Thus, we can only see the gold.

> 为了得到一个 1 像素高的椭圆，椭圆的宽度必须是 100,000 像素。但是我们最后的颜色停止只有 100 像素!此时，绘制的椭圆宽为 100 像素，高为 1000 像素。所有沿梯度光线从紫色到金色的过渡都必须在千分之一像素内发生。之后的所有东西都是金色的，就像最后的颜色一样。因此，我们只能看到黄金。

You might think that if you increased the position value of the last color stop to `100000px`, you’d see a thin sliver of purple-ish color running horizontally across the image. And you’d be right, `if` the browser treats `0px` as `0.001px` in these cases. If it assumes 0.`00000001px` instead, you’d have to increase the color stop’s position a `lot` further in order to see anything. And that’s assuming the browser was actually caulculating and drawing all those ellipses, instead of just hard-coding the special cases. The latter is a lot more likely, honestly. It’s what I’d do if I were in charge of a browser’s gradient-rendering code.

> 您可能会认为，如果您将最后一个颜色停止的位置值增加到“100000px”，您将看到一条细长的紫色横过图像。你是对的，如果浏览器在这些情况下把 0px 当作 0.001px。假设是 0。“00000001px”，相反，你必须增加颜色停止的位置'很多'为了看到任何东西。这是假设浏览器实际上在计算并绘制所有这些省略号，而不是硬编码特殊情况。老实说，后者可能性更大。如果我负责浏览器的渐变呈现代码，我就会这么做。

And what if an ellipse has zero width `and` zero height? In that case, the specification is written such that the zero-width behavior is used; thus, you’ll get the irrored-lineargradient behavior.

> 如果一个椭圆的宽度为 0，高度为 0 呢?在这种情况下，规范中使用了零宽度行为;因此，您将得到 irrored-lineargradient 行为。

<Tips tips="blue">As of late 2017, browser support for the defined behavior in these edge cases was unstable, at best. Some browsers used the last colorstop’s color in all cases, and others refused to draw a gradient at all in some cases.</Tips>

### 9.3.3 Manipulating Gradient Images

As has been emphasized (possibly to excess), gradients are images. That means you can size, position, repeat, and otherwise affect them with the various background properties, just as you would any PNG or SVG.

> 正如已经强调的(可能是过度的)，梯度是图像。这意味着您可以使用各种背景属性设置大小、位置、重复和其他方式影响它们，就像您可以使用任何 PNG 或 SVG 一样。

One way this can be leveraged is to repeat simple gradients. (Repeating in more complex ways is the subject of the next section.) For example, you could use a hard-stop radial gradient to give your background a dotted look, as shown in Figure 9-97:

> 可以利用这一点的一种方法是重复简单的渐变。(以更复杂的方式重复是下一节的主题。)例如，你可以使用一个硬停止径向梯度给你的背景一个虚线的外观，如图 9-97 所示:

```css
body {
  background: tan center/25px 25px repeat radial-gradient(circle at center, rgba(0, 0, 0, 0.1), rgba(
          0,
          0,
          0,
          0.1
        ) 10px, transparent 10px, transparent);
}
```

<Figures figure="9-98">Tiled radial gradient images</Figures>

Yes, this is visually pretty much the same as tiling a PNG that has a mostlytransparent dark circle 10 pixels in diameter. There are three advantages to using a gradient in this case:

> 是的，这在视觉上和平铺一个直径为 10 像素的透明暗圈的 PNG 差不多。在这种情况下使用渐变有三个优点:

- The CSS is almost certainly smaller in bytes than the PNG would be.
- Even more importantly, the PNG requires an extra hit on the server. This slows down both page and server performance. A CSS gradient is part of the stylesheet and so eliminates the extra server hit.
- Changing the gradient is a lot simpler, so experimenting to find exactly the right size, shape, and darkness is much easier.

---

> - CSS 在字节上几乎肯定比 PNG 要小。
> - 更重要的是，PNG 需要额外的服务器攻击。这会降低页面和服务器的性能。CSS 梯度是样式表的一部分，因此消除了额外的服务器攻击。
> - 改变渐变要简单得多，所以尝试找到正确的大小、形状和黑暗要容易得多。

Gradients can’t do everything a raster or vector image can, so it’s not as though you’ll be giving up external images completely now that gradients are a thing. You can still pull off some pretty impressive effects with gradients, though. Consider the background effect shown in Figure 9-99.

> 梯度并不能完成光栅或矢量图像所能完成的所有工作，因此，既然梯度已经成为了一种东西，那么就不能完全放弃外部图像。尽管如此，你仍然可以通过渐变获得一些令人印象深刻的效果。考虑图 9-99 所示的背景效果。

<Figures figure="9-99">It’s time to start the music…</Figures>

That curtain effect was accomplished with just two linear gradients repeated at differing intervals, plus a third to create a “glow” effect along the bottom of the background. Here’s the code that accomplished it:

> 窗帘效果是通过两个线性梯度重复在不同的间隔，加上第三个创建一个“辉光”效果沿背景底部。下面是实现它的代码:

```css
background-image: linear-gradient(
    0deg,
    rgba(255, 128, 128, 0.25),
    transparent 75%
  ), linear-gradient(
    89deg,
    transparent,
    transparent 30%,
    #510a0e 35%,
    #510a0e 40%,
    #61100f 43%,
    #b93f3a 50%,
    #4b0408 55%,
    #6a0f18 60%,
    #651015 65%,
    #510a0e 70%,
    #510a0e 75%,
    rgba(255, 128, 128, 0) 80%,
    transparent
  ), linear-gradient(92deg, #510a0e, #510a0e 20%, #61100f 25%, #b93f3a 40%, #4b0408
      50%, #6a0f18 70%, #651015 80%, #510a0e 90%, #510a0e);
background-size: auto, 300px 100%, 109px 100%;
background-repeat: repeat-x;
```

The first (and therefore topmost) gradient is just a fade from a 75%-transparent light red up to full transparency at the 75% point of the gradient line. Then two “fold” images are created. Figure 9-100 shows each separately.

> 第一个(因此也是最上面的)渐变只是从 75%透明的淡红色渐变到 75%完全透明的渐变线。然后创建两个“折叠”图像。图 9-100 分别显示了它们。

With those images defined, they are repeated along the x-axis and given different sizes. The first, which is the “glow” effect, is given `auto` size in order to let it cover the entire element background. The second is given a width of `300px` and a height of `100%`; thus, it will be as tall as the element background and 300 pixels wide. This means it will be tiled every 300 pixels along the x-axis. The same is true of the third image, except it tiles every 109 pixels. The end result looks like an irregular stage curtain.

> 定义了这些图像后，它们会沿着 x 轴重复，并给出不同的大小。第一个是“辉光”效果，为了让它覆盖整个元素背景，它被赋予了“自动”大小。第二个选项的宽度为“300px”，高度为“100%”;因此，它将与元素背景一样高，300 像素宽。这意味着它将沿 x 轴每 300 像素平铺一次。第三张也是如此，只是它每 109 个像素平铺一次。最终的效果就像一个不规则的舞台幕布。

<Figures figure="9-100">The two “fold” gradients</Figures>

The beauty of this is that adjusting the tiling intervals is just a matter of editing the stylesheet. Changing the color-stop positions or the colors is less trivial, but not too difficult if you know what effect you’re after. And adding a third set of repeating folds is no more difficult than just adding another gradient to the stack.

> 这样做的好处是，调整平铺间隔只需要编辑样式表。改变颜色停止的位置或颜色是不太容易的，但如果你知道你想要的效果，就不会太难。添加第三组重复折叠并不比在堆栈中添加另一个梯度更困难。

### 9.3.4 Repeating Gradients

Gradients are pretty awesome by themselves, but because they are images, they can be subject to strange behaviors when they are tiled. For example, if you declare:

> 渐变本身是非常棒的，但是因为它们是图像，所以它们在平铺时可能会有奇怪的行为。例如，如果你声明:

```css
h1.exmpl {
  background: linear-gradient(
      -45deg,
      black 0,
      black 25px,
      yellow 25px,
      yellow 50px
    ) top left/40px 40px repeat;
}
```

then you could easily end up with a situation like that shown in Figure 9-101.

> 然后，您很容易得到如图 9-101 所示的情况。

<Figures figure="9-101">Tiling gradient images with background-repeat</Figures>

As the figure shows, there is a discontinuity where the images repeat. You `could` try to nail down the exact sizes of the element and gradient image and then mess with the construction of the gradient image in order to try to make the sides line up, but it would be a lot better if there was just a way to say, “repeat this seamlessly forever.”

> 如图所示，有一个不连续的地方，图像重复。你“可能”试图确定元素的确切大小和梯度图像,然后惹的建设梯度图像为了试图让双方排队,但这将是一个更好如果只有一种方式说,“永远无缝地重复这个。”

Enter repeating gradients. For the previous example, all we need is to convert `linear-gradient` to `repeating-linear-gradient` and drop the `background-size` value.

> 输入重复的梯度。对于前面的示例，我们需要做的只是将' linear-gradient '转换为' repeat- linear-gradient '，并去掉' background-size '的值。

Everything else about the code stays the same. The effect is much different, however, as you can see in Figure 9-102:

> 代码的其他部分保持不变。但效果却大不相同，如图 9-102 所示:

```css
h1.exmpl {
  background: repeating-linear-gradient(
      -45deg,
      black 0,
      black 25px,
      yellow 25px,
      yellow 50px
    ) top left;
}
```

<Figures figure="9-102">A repeating gradient image with repeating-linear-gradient</Figures>

An equivalent to the previous code block, using color hints instead of all color stops, is:

> 与前一个代码块等价，使用颜色提示而不是所有颜色停止:

```css
h1.exmpl {
  background: repeating-linear-gradient(
      -45deg,
      black 0,
      black 25px,
      25px,
      yellow 50px
    ) top left;
}
```

What happens with a repeating linear gradient is that the declared color stops and color hints are repeated on a loop along the gradient line, over and over, forever. Given the previous examples, that means switching between black and yellow every 25 pixels forever.

> 重复的线性渐变所发生的情况是，所声明的颜色停止，颜色提示沿着渐变线重复循环，一遍又一遍，直到永远。根据前面的例子，这意味着每隔 25 个像素就会切换一次黑色和黄色。

Note that the last color stop has an explicit length (`50px`). This is important with repeating gradients, because the length value on the last color stop defines the overall length of the pattern.

> 注意，最后一个颜色停止有一个显式的长度(' 50px ')。这对于重复渐变非常重要，因为最后一个颜色停止的长度值定义了模式的总长度。

Now, those examples work because there’s supposed to be a hard stop where the gradient repeats. If you’re using smoother transitions, you need to be careful that the color value at the last color stop matches the color value at the first color stop. Consider this:

> 现在，这些例子是有效的因为在梯度重复的地方应该有一个困难的停止点。如果使用更平滑的过渡，需要注意最后一个颜色停止时的颜色值是否与第一个颜色停止时的颜色值匹配。考虑一下:

```css
repeating-linear-gradient(-45deg, purple 0px, gold 50px)
```

This will produce a smooth gradient from purple to gold at 50 pixels, and then a hard switch back to purple and another 50-pixel purple-to-gold blend. By adding one more color stop with the same color as the first color stop, the gradient can be smoothed out to avoid hard-stop lines. See Figure 9-103 for a comparison of the two approaches:

> 这将产生一个平滑的梯度从紫色到金色在 50 像素，然后一个硬切换回紫色和另一个 50 像素的紫色到金色混合。通过添加一个与第一个颜色停止相同颜色的颜色，梯度可以平滑，以避免硬停止线。两种方法的比较见图 9-103:

```css
repeating-linear-gradient(-45deg, purple 0px, gold 50px, purple 100px)
```

<Figures figure="9-103">Dealing with hard resets in repeating-gradient images</Figures>

You may have noticed that none of the repeating gradients we’ve seen so far have a defined size. That means the images are defaulting in size to the full background positioning area of the element to which they’re applied, per the default behavior for images that have no intrinsic height and width. If you were to resize a repeatinggradient image using `background-size`, the repeating gradient would only be visible within the gradient image. If you then repeated it using `background-repeat`, you could very easily be back to the situation of having discontinuities in your background, as illustrated in Figure 9-104:

> 您可能已经注意到，到目前为止我们所看到的重复渐变都没有定义大小。这意味着图像默认大小为应用它们的元素的整个背景定位区域，根据没有固有高度和宽度的图像的默认行为。如果你要使用“background-size”来调整一个重复渐变图像的大小，那么重复渐变只能在渐变图像中看到。如果您随后使用“background-repeat”重复它，您将非常容易回到您的背景中有不连续的情况，如图 9-104 所示:

```css
h1.exmpl {
  background: repeating-linear-gradient(
      -45deg,
      purple 0px,
      gold 50px,
      purple 100px
    ) top left/50px 50px repeat;
}
```

<Figures figure="9-104">Repeated tiling of repeating-gradient images</Figures>

If you use percentages in your repeating linear gradients, they’ll be placed the same as if the gradient wasn’t of the repeating variety. Then again, this would mean that all of the gradients defined by those color stops would be seen and none of the repetitions would be visible, so percentages are kind of pointless with repeating linear gradients.

> 如果您在重复线性梯度中使用百分比，它们的位置将与梯度不是重复变化时相同。再一次，这意味着所有由这些颜色停止定义的梯度将会被看到，并且没有任何重复将会被看到，所以百分比对于重复的线性梯度是没有意义的。

On the other hand, percentages can be very useful with repeating radial gradients, where the size of the circle or ellipse is defined, percentage positions along the gradient ray are defined, and you can see beyond the endpoint of the gradient ray. For example, assume:

> 另一方面，对于重复的径向梯度，百分比可能非常有用，其中定义了圆形或椭圆的大小，定义了沿梯度射线的百分比位置，您可以看到梯度射线的端点之外。例如,假设:

```css
.allhail {
  background: repeating-radial-gradient(
    100px 50px,
    purple,
    gold 20%,
    green 40%,
    purple 60%,
    yellow 80%,
    purple
  );
}
```

Given this rule, there will be a color stop every 20 pixels, with the colors repeating in the declared pattern. Because the first and last color stops have the same color value, there is no hard color switch. The ripples just spread out forever, or at least until they’re beyond the edges of the gradient image. See Figure 9-105 for an example.

> 根据这一规则，每 20 个像素将有一个颜色停止，颜色重复声明的模式。因为第一个和最后一个颜色停止有相同的颜色值，没有硬的颜色开关。这些涟漪会一直扩散下去，或者至少会扩散到渐变图像的边缘。参见图 9-105 中的示例。

<Figures figure="9-105">Repeating radial gradients</Figures>

Just imagine what that would look like with a repeating radial gradient of a rainbow!

> 想象一下彩虹重复的径向梯度会是什么样子!

```css
.wdim {
  background: repeating-radial-gradient(
    100px circle at bottom center,
    rgb(83%, 83%, 83%) 50%,
    violet 55%,
    indigo 60%,
    blue 65%,
    green 70%,
    yellow 75%,
    orange 80%,
    red 85%,
    rgb(47%, 60%, 73%) 90%
  );
}
```

There are a couple of things to keep in mind when creating repeating radial gradients:

> 在创建重复的径向梯度时要记住以下几点:

- If you don’t declare size dimensions for a radial, it will default to an ellipse that has the same height-to-width ratio as the overall gradient image; `and`, if you don’t declare a size for the image with `background-size`, the gradient image will default to the height and width of the element background where it’s being applied. (Or, in the case of being used as a list-style bullet, the size that the browser gives it.)
- The default radial size value is `farthest-corner`. This will put the endpoint of the gradient ray far enough to the right that its ellipse intersects with the corner of the gradient image that’s furthest from the center point of the radial gradient.

---

> - 如果你不声明径向尺寸尺寸，它将默认为一个椭圆，有相同的高度与宽度比作为整体梯度图像;'和'，如果你没有声明图像的大小与' background-size '，梯度图像将默认为高度和宽度的元素背景，它被应用。(或者，如果使用列表样式的项目符号，浏览器给出的大小。)
> - 默认的径向尺寸值是'最远的角落'。这将把梯度射线的端点放在足够远的右边，使其椭圆与梯度图像的角相交，这是距离径向梯度中心点最远的地方。

These are reiterated here to remind you that if you stick to the defaults, there’s not really any point to having a repeating gradient, since you’ll only be able to see the first iteration of the repeat. It’s only when you restrict the initial size of the gradient that the repeats become visible.

> 这里重申一下，提醒您如果坚持使用默认值，实际上没有必要使用重复梯度，因为您只能看到 repeat 的第一次迭代。只有当你限制梯度的初始大小时，重复才会变得可见。

<Tips tips="orange">Radial gradients, and in particular repeating radial gradients, created massive performance drains in older mobile devices. Crashes were not uncommon in these situations, and both page rendering time and battery performance could suffer greatly. Think very, very carefully about using radial gradients in mobile contexts, and be sure to rigorously test their performance and stability in any context, especially if you have users with older devices (and therefore older browsers).</Tips>

#### Average gradient colors

Another edge case is what happens if a repeating gradient’s first and last color stops somehow end up being in the same place. For example, suppose your fingers missed the “5” key and you accidentally declared the following:

> 另一种情况是，如果重复渐变的第一个和最后一个颜色以某种方式停止在同一个地方，会发生什么。例如，假设您的手指错过了“5”键，并且您意外地声明了以下内容:

```css
repeating-radial-gradient(center, purple 0px, gold 0px)
```

The first and last color stops are zero pixels apart, but the gradient is supposed to repeat ad infinitum along the gradient line. Now what?

> 第一个和最后一个颜色停止点之间的距离为零像素，但是梯度应该沿着梯度线无限重复。现在怎么办呢?

In such a case, the browser finds the average gradient color and fills it in throughout the entire gradient image. In our simple case in the preceding code, that will be a 50/50 blend of purple and `gold` (which will be about `#C06C40` or `rgb(75%,42%,25%)`). Thus, the resulting gradient image should be a solid orangey-brown, which doesn’t really look much like a gradient.

> 在这种情况下，浏览器找到平均梯度颜色，并在整个梯度图像中填充它。在前面代码中的简单示例中，紫色和“金色”的比例为 50/50(约为“#C06C40”或“rgb(75%、42%、25%)”)。因此，生成的渐变图像应该是一个固体的橙棕色，这看起来不太像渐变。

This condition can also be triggered in cases where the browser rounds the color-stop positions to zero, or cases where the distance between the first and last color stops is so small as compared to the output resolution that nothing useful can be rendered. This could happen if, for example, a repeating radial gradient used all percentages for the color-stop positions and was sized using `closest-side`, but was accidentally placed into a corner.

> 如果浏览器将颜色停止位置舍入为零，或者第一个颜色停止与最后一个颜色停止之间的距离与输出分辨率相比非常小，以致于无法呈现任何有用的内容，也可以触发此条件。这可能会发生，例如，一个重复的径向梯度使用所有的百分比的颜色停止位置和大小使用“最接近的一面”，但不小心被放置到一个角落。

<Tips tips="orange">As of late 2017, no browsers really do this correctly. It is possible to trigger some of the correct behaviors under very limited conditions, but in most cases, browsers either just use the last color stop as a fill color, or else try really hard to draw sub-pixel repeating patterns.</Tips>

## 9.4 Box Shadows

In an earlier chapter, we explored the property `text-shadow`, which adds a drop shadow to the text of a non-replaced element. There’s a version of this that creates a shadow for the box of an element, called `box-shadow`.

> 在前一章中，我们探讨了属性“text-shadow”，它为不可替换元素的文本添加了一个投影。有一个这样的版本，它为一个元素的盒子创建一个阴影，叫做“box-shadow”。

<Cards cards="box-shadow" />

It might seem a little out of place to talk about shadows in a chapter mostly concerned with backgrounds and gradients, but there’s a reason it goes here, which we’ll see in a moment.

> 在一个主要涉及背景和渐变的章节中讨论阴影似乎有点不合适，但是在这里讨论它是有原因的，我们稍后会看到。

Let’s consider a simple box drop shadow: one that’s 10 pixels down and 10 pixels to the right of an element box, with no spread or blur, and a half-opaque black. Behind it we’ll put a repeating background on the `body` element. All of this is illustrated in Figure 9-106.

> 让我们考虑一个简单的 box drop shadow:一个是向下 10 个像素，在元素框的右边 10 个像素处，没有扩展或模糊，并且是半不透明的黑色。在它后面，我们将在“body”元素上放置一个重复的背景。所有这些都在图 9-106 中进行了说明。

```css
#box {
  background: silver;
  border: medium solid;
  box-shadow: 10px 10px rgba(0, 0, 0, 0.5);
}
```

<Figures figure="9-106">A simple box shadow</Figures>

We can see that the `body`’s background is visible through the half-opaque (or halftransparent, if you prefer) drop shadow. Because no blur or spread distances were defined, the drop shadow exactly mimics the outer shape of the element box itself. At least, it appears to do so.

> 我们可以看到，“身体”的背景是可见的，通过半不透明(或半透明，如果你喜欢)投影。由于没有定义模糊或扩展距离，投影完全模拟元素盒本身的外部形状。至少看起来是这样的。

The reason it only appears to mimc the shape of the box is that the shadow is only visible outside the outer border edge of the element. We couldn’t really see that in the previous figure, because the element had an opaque background. You might have just assumed that the shadow extended all the way under the element, but it doesn’t. Consider the following, illustrated in Figure 9-107.

> 它只能模仿盒子的形状的原因是阴影只能在元素的外边界边缘看到。在之前的图中我们并不能真正看到它，因为元素的背景是不透明的。你可能认为阴影一直延伸到元素下面，但事实并非如此。考虑如下图 9-107 所示的情况。

```css
#box {
  background: transparent;
  border: thin dashed;
  box-shadow: 10px 10px rgba(0, 0, 0, 0.5);
}
```

<Figures figure="9-107">Box shadows are incomplete</Figures>

So it looks as though the element’s content (and padding and border) area “knocks out” part of the shadow. In truth, it’s just that the shadow was never drawn there, due to the way box shadows are defined in the specification. This does mean, as Figure 9-107 demonstrates, that any background “behind” the box with a drop shadow can be visible through the element itself. This (perhaps bizarre-seeming) interaction with the backgrounds and borders is why `box-shadow` is covered here, instead of at an earlier point in the text.

> 所以看起来好像元素的内容(以及填充和边框)区域“敲除”了阴影的一部分。事实上，只是阴影从来没有画在那里，因为在规范中定义了框阴影的方式。这意味着，如图 9-107 所示，任何有阴影的背景都可以通过元素本身看到。这种与背景和边框的交互作用(可能看起来很奇怪)就是为什么“box-shadow”在这里被覆盖，而不是在文本的前面。

So far, we’ve seen box shadows defined with two length values. The first defines a horizontal offset, and the second a vertical offset. Positive numbers move the shadow down and to right right, and negative numbers move the shadow up and to the left.

> 到目前为止，我们已经看到了用两个长度值定义的框阴影。第一个定义水平偏移量，第二个定义垂直偏移量。正数把影子移向右下方，负数把影子移向左上方。

If a third length is given, it defines a blur distance, which determines how much space is given to blurring. A fourth length defines a spread distance, which change the size of the shadow. Positive length values make the shadow expand before blurring happens; negative values cause the shadow to shrink. The following have the results shown in Figure 9-108.

> 如果给出了第三个长度，它定义了一个模糊距离，这个距离决定了给模糊多少空间。第四个长度定义了一个扩展距离，它改变了阴影的大小。正的长度值使阴影在模糊之前扩大;负值会导致阴影缩小。下面的结果如图 9-108 所示。

```css
.box:nth-of-type(1) {
  box-shadow: 1em 1em 2px rgba(0, 0, 0, 0.5);
}
.box:nth-of-type(2) {
  box-shadow: 2em 0.5em 0.25em rgba(128, 0, 0, 0.5);
}
.box:nth-of-type(3) {
  box-shadow: 0.5em 2ch 1vw 13px rgba(0, 128, 0, 0.5);
}
.box:nth-of-type(4) {
  box-shadow: -10px 25px 5px -5px rgba(0, 128, 128, 0.5);
}
.box:nth-of-type(5) {
  box-shadow: 0.67em 1.33em 0 -0.1em rgba(0, 0, 0, 0.5);
}
.box:nth-of-type(6) {
  box-shadow: 0.67em 1.33em 0.2em -0.1em rgba(0, 0, 0, 0.5);
}
.box:nth-of-type(7) {
  box-shadow: 0 0 2ch 2ch rgba(128, 128, 0, 0.5);
}
```

<Figures figure="9-108">Various blurred and spread shadows</Figures>

You may have noticed that some of the boxes in Figure 9-108 have rounded corners (via `border-radius`), and that their shadows were curved to match. This is the defined behavior, fortunately.

> 您可能已经注意到图 9-108 中的一些盒子有圆角(通过“border-radius”)，它们的阴影是弯曲的。幸运的是，这是定义的行为。

There’s one aspect of `box-shadow` we have yet to cover, which is the `inset` keyword. If `inset` is added to the value of `box-shadow`, then the shadow is rendered inside the box, as if the box were a punched-out hole in the canvas rather than floating above it (visually speaking). Let’s take the previous set of examples and redo them with inset shadows. This will have the result shown in Figure 9-109.

> “box-shadow”有一个方面我们还没有涉及，那就是“inset”关键字。如果“inset”被添加到“box-shadow”的值中，那么阴影就会被呈现在盒子里，就好像盒子是画布上的一个打出来的洞，而不是漂浮在上面(从视觉上来说)。让我们以前面的例子为例，用 inset shadows 重做它们。结果如图 9-109 所示。

```css
.box:nth-of-type(1) {
  box-shadow: inset 1em 1em 2px rgba(0, 0, 0, 0.5);
}
.box:nth-of-type(2) {
  box-shadow: inset 2em 0.5em 0.25em rgba(128, 0, 0, 0.5);
}
.box:nth-of-type(3) {
  box-shadow: 0.5em 2ch 1vw 13px rgba(0, 128, 0, 0.5) inset;
}
.box:nth-of-type(4) {
  box-shadow: inset -10px 25px 5px -5px rgba(0, 128, 128, 0.5);
}
.box:nth-of-type(5) {
  box-shadow: 0.67em 1.33em 0 -0.1em rgba(0, 0, 0, 0.5) inset;
}
.box:nth-of-type(6) {
  box-shadow: inset 0.67em 1.33em 0.2em -0.1em rgba(0, 0, 0, 0.5);
}
.box:nth-of-type(7) {
  box-shadow: 0 0 2ch 2ch rgba(128, 128, 0, 0.5) inset;
}
```

<Figures figure="9-109">Various inset shadows</Figures>

Note that the `inset` keyword can appear before the rest of the value, or after, but `not` in the middle of the lengths and colors. A value like 0 0 0.1em inset gray would be ignored as invalid, because of the placement of the `inset` keyword.

> 请注意，' inset '关键字可以出现在值的其余部分之前或之后，但' not '不能出现在长度和颜色中间。像 0 0 0.1em inset gray 这样的值将被忽略，因为它是无效的，这是因为‘inset’关键字的位置。

The last thing to note is that you can apply to an element a list of as many commaseparated box shadows as you like, just as with text shadows. Some could be inset, and some outset. The following rules are just two of the infinite possibilities.

> 最后要注意的是，您可以向元素应用任意数量的与 commaseparated box shadows，就像文本阴影一样。有些可以嵌入，有些可以开始。下面的规则只是无限可能性中的两个。

```css
#shadowbox {
  background: #eee;
  box-shadow: inset 1ch 1ch 0.25ch rgba(0, 0, 0, 0.25), 1.5ch 1.5ch 0.4ch rgba(0, 0, 0, 0.33);
}
#wacky {
  box-shadow: inset 10px 2vh 0.77em 1ch red, 1cm 1in 0 -1px cyan inset,
    2ch 3ch 0.5ch hsla(117, 100%, 50%, 0.343), -2ch -3ch 0.5ch hsla(297, 100%, 50%, 0.23);
}
```

<Tips tips="green">The <code>filter</code> property is another way to create element drop shadows, although it is much closer in behavior to <code>text-shadow</code> than <code>box-shadow</code>, albeit applying to the entire element box and text. See Chapter 19 for details.</Tips>

## 9.5 Summary

Setting colors and backgrounds on elements gives authors a great deal of power. The advantage of CSS over traditional methods is that colors and backgrounds can be applied to any element in a document.

> 在元素上设置颜色和背景给了作者很大的力量。与传统方法相比，CSS 的优势在于颜色和背景可以应用于文档中的任何元素。
