# 第 6 章 文本属性 Text Properties

Sure, a lot of web design involves picking the right colors and getting the coolest look for your pages, but when it comes right down to it, you probably spend more of your time worrying about where text will go and how it will look. Such concerns gave rise to HTML tags such as `<FONT>` and `<CENTER>` in the web’s early days, which allowed you some measure of control over the appearance and placement of text.

> 当然，很多网页设计都涉及到选择正确的颜色和让页面看起来最酷，但是当你真正开始做的时候，你可能会花更多的时间去担心文本的位置和外观。这样的担忧导致了 HTML 标签的出现，如 `<FONT>` 和 `<CENTER>` 在 web 的早期，这允许您对文本的外观和位置进行一定程度的控制。

Because text is so important, there are many CSS properties that affect it in one way or another. What is the difference between text and fonts? At the simplest level, text is the content, and fonts are used to display that content. Using text properties, you can affect the position of text in relation to the rest of the line, superscript it, underline it, and change the capitalization. You can even simulate, to a limited degree, the use of a typewriter’s Tab key.

> 因为文本是如此重要，所以有许多 CSS 属性会以这样或那样的方式影响它。文本和字体有什么区别?在最简单的层次上，文本是内容，字体用于显示该内容。使用文本属性，您可以影响文本相对于行的其余部分的位置、给它加上上标、下划线并更改大小写。你甚至可以在一定程度上模拟使用打字机的 Tab 键。

## 6.1 Indentation and Inline Alignment

Let’s start with a discussion of how you can affect the inline positioning of text within a line. Think of these basic actions as the same types of steps you might take to create a newsletter or write a report.

> 让我们首先讨论如何影响文本在一行中的内联定位。把这些基本的行动想成是你创建时事通讯或写报告的相同类型的步骤。

First, however, let’s take a moment to talk about the terms `inline` and `block` as they’ll be used in this chapter. In fact, let’s take them in reverse. If your primary language is Western-derived, then you’re used to a block direction of top to bottom, and an inline direction of left to right. Let’s examine those terms more closely.

> 但是，首先，让我们花点时间讨论一下术语“inline”和“block”，因为它们将在本章中使用。实际上，我们把它们反过来。如果您的主要语言是西方派生的，那么您将习惯于从上到下的块方向，以及从左到右的内联方向。让我们更仔细地研究这些术语。

The `block direction` is the direction in which block elements are placed by default in the current writing mode. In English, for example, the block direction is top to bottom, or vertical, as one paragraph (or other text element) is placed beneath the one before.

> “块方向”是块元素在当前写入模式下默认放置的方向。例如，在英语中，块的方向是从上到下，或者是垂直的，因为一个段落(或其他文本元素)放在前面一个段落的下面。

The `inline direction` is the direction in which inline elements are written within a block. To again take English as an example, the inline direction is left to right, or horizontal. In languages like Arabic and Hebrew, the inline direction is right to left instead.

> “内联方向”是在一个块中写入内联元素的方向。再以英语为例，行内方向是从左到右，或水平方向。在阿拉伯语和希伯来语等语言中，内联方向是从右到左。

Let’s reconsider English for a moment. A plain page of English text, displayed on a screen, has a vertical block direction and a horizontal inline direction. But if the page is rotated 90 degrees anticlockwise using CSS Transforms, then suddenly the block direction is horizontal and the inline direction is vertical. (And bottom to top, at that.)

> 让我们重新考虑一下英语。显示在屏幕上的纯英文文本页具有垂直块方向和水平内联方向。但是，如果使用 CSS 转换将页面逆时针旋转 90 度，那么块方向就会突然变为水平方向，而内联方向则变为垂直方向。(从下到上，就是这样。)

This approach to content and layout is relatively new as of 2017, and a conversion from the old layout language, which was highly dependent on concepts of “horizontal” and “vertical,” is still underway. While the rest of the chapter will try to use the terms “block direction” and “inline direction,” please forgive any lapses into “vertical” and “horizontal.”

> 从 2017 年开始，这种内容和布局的方法相对较新，从高度依赖“水平”和“垂直”概念的旧布局语言的转换仍在进行中。虽然本章的其余部分将尝试使用术语“块方向”和“内联方向”，请原谅在“垂直”和“水平”上的任何错误。

### 6.1.1 Indenting Text

Most books we read in Western languages format paragraphs of text with the first line indented, and no blank line between paragraphs. Some sites used to create the illusion of indented text by placing a small transparent image before the first letter in a paragraph, which shoved the text over. Thanks to CSS, there’s a much better way to indent text: `text-indent`.

> 我们读的大多数西方语言的书，段落的格式都是第一行缩进，段落之间没有空行。一些网站通过在一个段落的第一个字母前放置一个透明的小图像来产生缩进文本的效果，这将文本挤到了一起。感谢 CSS，有一个更好的方式来缩进文本:' text-indent '。

<Cards cards="text-indent" />

Using `text-indent`, the first line of any element can be indented by a given length, even if that length is negative. A common use for this property is to indent the first line of a paragraph:

> 使用“text-indent”，任何元素的第一行都可以按给定长度缩进，即使该长度是负数。这个属性的一个常见用法是缩进段落的第一行:

```css
p {
  text-indent: 3em;
}
```

This rule will cause the first line of any paragraph to be indented three ems, as shown in Figure 6-1.

> 此规则将导致任何段落的第一行缩进三个ems，如图6-1所示。

<Figures figure="6-1">Text indenting</Figures>

In general, you can apply `text-indent` to any element that generates a block box, and the indentation will occur along the inline direction. You can’t apply it to inline elements or on replaced elements such as images. However, if you have an image within the first line of a block-level element, it will be shifted over with the rest of the text in the line.

> 通常，您可以将“text-indent”应用于生成块框的任何元素，并且缩进将沿着内联方向发生。您不能将其应用到内联元素或替换的元素(如图像)上。但是，如果在块级别元素的第一行中有一个图像，那么它将与该行中的其他文本一起移动。

<Tips tips="blue">If you want to “indent” the first line of an inline element, you can create the effect with left padding or margin.</Tips>

You can also set negative values for `text-indent`, a technique that leads to a number of interesting effects. The most common use is a hanging indent, where the first line hangs out to one side of the rest of the element:

> 您还可以为“text-indent”设置负值，这种技术可以产生许多有趣的效果。最常见的用法是挂缩进，第一行挂在元素其余部分的一侧:

```css
p {
  text-indent: −4em;
}
```

Be careful when setting a negative value for `text-indent`; the first few words may be chopped off by the edge of the browser window if you aren’t careful. To avoid display problems, I recommend you use a margin or some padding to accommodate the negative indentation:

> 为“text-indent”设置负值时要小心;如果你不小心的话，开头的几个字可能会被浏览器窗口边缘截断。为了避免显示问题，我建议您使用空白或一些填充来容纳负缩进:

```css
p {
  text-indent: −4em;
  padding-left: 4em;
}
```

Negative indents can, however, be used to your advantage. Consider the following example, demonstrated in Figure 6-2, which adds a floated image to the mix:

> 然而，负缩进可以利用你的优势。考虑下面的例子，如图 6-2 所示，它将一个浮动的图像添加到混合中:

```css
p.hang {
  text-indent: −25px;
}
```

```html
<img
  src="star.gif"
  style="width: 60px; height: 60px;
float: left;"
  alt="An image of a five-pointed star."
/>
<p class="hang">
  This paragraph has a negatively indented first line, which overlaps the
  floated image that precedes the text. Subsequent lines do not overlap the
  image, since they are not indented in any way.
</p>
```

<Figures figure="6-2">A floated image and negative text indenting</Figures>

A variety of interesting designs can be achieved using this simple technique.

> 使用这种简单的技术可以实现各种有趣的设计。

<Tips tips="blue">This specific effect, of trying to make text wrap along the edge of a loated image, is more robustly managed with CSS Float Shapes. See Chapter 10 for details.</Tips>

Any unit of length, including percentage values, may be used with `text-indent`. In the following case, the percentage refers to the width of the parent element of the element being indented. In other words, if you set the indent value to `10%`, the first line of an affected element will be indented by 10 percent of its parent element’s width, as shown in Figure 6-3:

> 任何长度单位，包括百分比值，都可以与“text-缩进”一起使用。在下面的例子中，百分比表示被缩进的元素的父元素的宽度。换句话说，如果您将缩进值设置为“10%”，则受影响元素的第一行将被其父元素宽度的 10%缩进，如图 6-3 所示:

```css
div {
  width: 400px;
}
p {
  text-indent: 10%;
}
```

```html
<div>
  <p>
    This paragraph is contained inside a DIV, which is 400px wide, so the first
    line of the paragraph is indented 40px (400 * 10% = 40). This is because
    percentages are computed with respect to the width of the element.
  </p>
</div>
```

<Figures figure="6-3">Text indenting with percentages</Figures>

Note that this indentation only applies to the first line of an element, even if you insert line breaks. The interesting part about `text-indent` is that because it’s inherited, it can have unexpected effects. For example, consider the following markup, which is illustrated in Figure 6-4:

> 注意，这种缩进仅适用于元素的第一行，即使您插入了换行符。“文本缩进”的有趣之处在于，因为它是继承的，所以会产生意想不到的效果。例如，考虑下面的标记，如图 6-4 所示:

```css
div#outer {
  width: 500px;
}
div#inner {
  text-indent: 10%;
}
p {
  width: 200px;
}
```

```html
<div id="outer">
  <div id="inner">
    This first line of the DIV is indented by 50 pixels.
    <p>
      This paragraph is 200px wide, and the first line of the paragraph is
      indented 50px. This is because computed values for 'text-indent' are
      inherited, instead of the declared values.
    </p>
  </div>
</div>
```

<Figures figure="6-4">Inherited text indenting</Figures>

### 6.1.2 Text Alignment

Even more basic than `text-indent` is the property `text-align`, which affects how the lines of text in an element are aligned with respect to one another.

> 比“text-indent”更基本的属性是“text-align”，它影响元素中的文本行之间的对齐方式。

<Cards cards="text-align" />

The quickest way to understand how these values work is to examine Figure 6-5, which sticks with three most widely supported values for the moment.

> 理解这些值如何工作的最快方法是查看图 6-5，它暂时坚持使用三个得到广泛支持的值。

<Figures figure="6-5">Selected behaviors of the text-align property</Figures>

The values `left`, `right`, and `center` cause the text within elements to be aligned exactly as described. Because `text-align` applies only to block-level elements, such as paragraphs, there’s no way to center an anchor within its line without aligning the rest of the line (nor would you want to, since that would likely cause text overlap).

> 值“left”、“right”和“center”将导致元素内的文本完全按照描述对齐。因为“文本对齐”只适用于块级别的元素，比如段落，所以锚点不可能在其行中居中而不对齐该行的其他部分(您也不希望这样，因为这可能会导致文本重叠)。

Historically, which is to say under CSS 2.1 rules, the default value of `text-align` is `left` in left-to-right languages, and `right` in right-to-left languages. (CSS 2.1 had no notion of vertical writing modes.) In CSS3, `left` and `right` are mapped to the start or end edge, respectively, of a vertical language. This is illustrated in Figure 6-6.

> 从历史上看，也就是说在 CSS 2.1 规则下，“文本对齐”的默认值是“左”(从左到右)，“右”(从右到左)。(css2.1 没有垂直书写模式的概念。)在 CSS3 中，“左”和“右”分别映射到垂直语言的起始或结束边缘。如图 6-6 所示。

<Figures figure="6-6">Left, right, and center in vertical writing modes</Figures>

As you no doubt expect, `center` causes each line of text to be centered within the element. Although you may be tempted to believe that `text-align: center` is the same as the `<CENTER>` element, it’s actually quite different. `<CENTER>` affected not only text, but also centered whole elements, such as tables. `text-align` does not control the alignment of elements, only their inline content. Figures 6-5 and 6-6 illustrate this clearly in various writing directions.

> 如您所料，' center '将使元素中的每行文本居中。尽管您可能会认为 text-align: center 与 `<CENTER>` 元素相同，但它实际上是完全不同的。`<CENTER>` 不仅影响文本，还影响整个元素的居中，如表。“文本对齐”不控制元素的对齐，只控制它们的内联内容。图 6-5 和图 6-6 清楚地说明了这一点。

#### Start and end alignment

CSS3 (which is to say, the CSS Text Module Level 3 specification) added a number of new values to `text-align`, and even changed the default property value as compared to CSS 2.1.

> CSS3(即 CSS Text Module Level 3 规范)为“Text -align”添加了许多新值，甚至与 CSS 2.1 相比改变了默认属性值。

The new default value of `start` means that the text is aligned to the start edge of its line box. In left-to-right languages like English, that’s the left edge; in right-to-left languages such as Arabic, it’s the right edge. In vertical languages, for that matter, it will be the top or bottom, depending on the writing direction. The upshot is that the default value is much more aware of the document’s language direction while leaving the default behavior the same in the vast majority of existing cases.

> 新的默认值“start”表示文本对齐到其行框的开始边缘。在从左到右的语言中，比如英语，这是左边缘;在阿拉伯语等从右向左的语言中，它是右边缘。在垂直语言中，根据书写方向，它将是顶部或底部。其结果是，默认值更清楚文档的语言方向，而在绝大多数现有情况下保持默认行为不变。

In a like manner, `end` aligns text with the end edge of each line box—the right edge in LTR languages, the left edge in RTL languages, and so forth. The effects of these values are shown in Figure 6-7.

> 以类似的方式，“end”将文本与每个行框的结束边缘对齐—在 LTR 语言中是右边缘，在 RTL 语言中是左边缘，等等。这些值的效果如图 6-7 所示。

<Figures figure="6-7">Start and end alignment</Figures>

#### Justified text

An often-overlooked alignment value is `justify`, which raises some issues of its own. In justified text, both ends of a line of text are placed at the inner edges of the parent element, as Figure 6-8 shows. Then, the spacing between words and letters is adjusted so that each line is precisely the same length. Justified text is common in the print world (for example, in this book), but under CSS, a few extra considerations come into play.

> 一个经常被忽视的对齐值是“证明”，它本身会引起一些问题。在对齐的文本中，一行文本的两端都位于父元素的内部边缘，如图 6-8 所示。然后，调整单词和字母之间的间距，使每一行的长度完全相同。文本对齐在打印环境中很常见(例如，在本书中)，但是在 CSS 下，需要考虑一些额外的因素。

<Figures figure="6-8">Justified text</Figures>

The user agent—and not CSS, at least as of late 2017—determines how justified text should be stretched to fill the space between the left and right edges of the parent. Some browsers, for example, might add extra space only between words, while others might distribute the extra space between letters (although the CSS specification states that “user agents may not further increase or decrease the inter-character space” if the property `letter-spacing` has been assigned a length value). Other user agents may reduce space on some lines, thus mashing the text together a bit more than usual. All of these possibilities will affect the appearance of an element, and may even change its height, depending on how many lines of text result from the user agent’s justification choices.

> 用户代理(而不是 CSS，至少在 2017 年年底)决定如何拉伸文本以填充父元素左右边缘之间的空间。一些浏览器,例如,单词之间可能只添加额外的空间,而其他人可能会分配额外的空间之间的信件(尽管 CSS 规范指出,“用户代理可能不会进一步增加或减少 inter-character 空间”如果已经指定了房地产的字母间距长度值)。其他用户代理可能会减少某些行上的空间，从而比通常更多地混合文本。所有这些可能性都将影响元素的外观，甚至可能改变其高度，这取决于用户代理的对齐选择产生多少行文本。

<Tips tips="blue">There is a property meant to provide authors more say over how full justification is accomplished: <code>text-justify</code>. As of late 2017, it was barely supported in any browser, with plans to add it to Firefox and some buggy experimental work in Chrome.</Tips>

#### Parent matching

There’s one more value to be covered, which is `match-parent`. This isn’t supported by browsers, but its intent is mostly covered by `inherit` anyway. The idea is, if you declare `text-align: match-parent`, the alignment of the element will match the alignment of its parent.

> 还有一个值需要覆盖，即“match-parent”。浏览器不支持这个功能，但它的意图主要是通过“继承”来实现的。其思想是，如果您声明“text-align: match-parent”，则元素的对齐方式将与其父元素的对齐方式匹配。

So far, that sounds exactly like `inherit`, but there’s a difference: if the parent’s alignment value is `start` or `end`, the result of `match-parent` is to assign a computed value of `left` or `right` to the element. That wouldn’t happen with `inherit`, which would apply `start` or `end` to the element with no changes.

> 到目前为止，这听起来与“inherit”完全相同，但有一个区别:如果父元素的对齐值是“start”或“end”，则“match-parent”的结果是将计算得到的值“left”或“right”分配给元素。在“inherit”中不会发生这种情况，因为它会将“start”或“end”应用到元素上，而不会发生任何更改。

<Tips tips="orange">The value <code>start end</code>, while technically part of the <code>text-align</code> syntax in late 2017, is not covered because it remains unimplemented and is at risk of being dropped from the specification.</Tips>

### 6.1.3 Aligning the Last Line

There may be times when you want to align the text in the very last line of an element differently than you did the rest of the content. For example, you might left-align the last line of an otherwise fully justified block of text, or choose to swap from left to center alignment. For those situations, there is `text-align-last`.

> 有时，您可能希望将元素最后一行的文本与其他内容的对齐方式不同。例如，可以左对齐完全对齐的文本块的最后一行，或者选择从左到中对齐。对于这些情况，有 `text-align-last`。

<Cards cards="text-align-last" />

As with `text-align`, the quickest way to understand how these values work is to examine Figure 6-9.

> 与“文本对齐”一样，理解这些值如何工作的最快方法是查看图 6-9。

<Figures figure="6-9">Differently aligned last lines</Figures>

As the figure shows, the last lines of the elements are aligned independently of the rest of the elements, according to the elements’ `text-align-last` values.

> 如图所示，根据元素的“text-align-last”值，元素的最后几行独立于其他元素对齐。

A close study of Figure 6-9 will reveal that there’s more at play than just the last lines of block-level elements. In fact, `text-align-last` applies to any line of text that immediately precedes a forced line break, whether or not said line break is triggered by the end of an element. Thus, a line break occasioned by a `<br>` tag will make the line of text immediately before that break use the value of `text-align-last`. So too will it affect the last line of text in a block-level element, since a line break is generated by the element’s closure.

> 仔细研究图 6-9 将会发现，除了块级元素的最后几行之外，还有更多的东西在起作用。实际上，“text-align-last”适用于紧接强制换行之前的任何一行文本，无论该换行是否由元素的末尾触发。因此，由 `<br>` 标记引起的换行符将使紧接在换行符之前的文本行使用“text-align-last”值。它也会影响块级元素中的最后一行文本，因为行分隔符是由元素的闭包生成的。

There’s an interesting wrinkle in `text-align-last`: if the first line of text in an element is also the last line of text in the element, then the value of `text-align-last` takes precedence over the value of `text-align`. Thus, the following styles will result in a centered paragraph, not a start-aligned paragraph:

> “text-align-last”中有一个有趣的问题:如果元素中的第一行文本也是元素中的最后一行文本，那么“text-align-last”的值将优先于“text-align”的值。因此，以下的风格将导致一个居中段落，而不是一个开始对齐的段落:

```css
p {
  text-align: start;
  text-align-last: center;
}
```

```html
<p>A paragraph.</p>
```

<Tips tips="orange">As of late 2017, support for <code>text-align-last</code> was missing in Safari and Opera Mini, and Internet Explorer and Edge only supported <code>left</code>, <code>right</code>, and <code>center</code>.</Tips>

## 6.2 Inline Alignment

Now that we’ve covered alignment along the inline direction, let’s move on to the vertical alignment of inline elements along the block direction—things like superscripting and “vertical alignment,” as it’s called. (Vertical with respect to the line of text, if the text is laid out horizontally.) Since the construction of lines is a very complex topic that merits its own small book, I’ll just stick to a quick overview here.

> 现在我们已经讨论了沿内联方向的对齐，接下来让我们讨论沿块方向的内联元素的垂直对齐—诸如上标和所谓的“垂直对齐”。(垂直于文本行，如果文本是水平放置的。)由于构建行是一个非常复杂的主题，值得编写一本小型的书，所以我只在这里简要介绍一下。

### 6.2.1 The Height of Lines

The distance between lines can be affected by changing the “height” of a line. note that “height” here is with respect to the line of text itself, assuming that the longer axis of a line is “width” even if it’s written vertically. The property names we cover from here will reveal a strong bias toward Western languages and their writing directions; this is an artifact of the early days of CSS, when Western languages were the only ones that could be easily represented.

> 线与线之间的距离可以通过改变线的“高度”来影响。请注意，这里的“高度”是相对于文本行本身的，假设一行的长轴是“宽度”，即使它是垂直书写的。我们从这里涵盖的属性名称将揭示出对西方语言及其写作方向的强烈偏见;这是 CSS 早期的产物，当时西方语言是唯一可以轻松表示的语言。

The `line-height` property refers to the distance between the baselines of lines of text rather than the size of the font, and it determines the amount by which the height of each element’s box is increased or decreased. In the most basic cases, specifying `line-height` is a way to increase (or decrease) the vertical space between lines of text, but this is a misleadingly simple way of looking at how `line-height` works. `line-height` controls the `leading`, which is the extra space between lines of text above and beyond the font’s size. In other words, the difference between the value of `line-height` and the size of the font is the leading.

> “行高”属性是指文本行的基线之间的距离，而不是字体的大小，它决定每个元素框的高度增加或减少的数量。在最基本的情况下，指定' line-height '是增加(或减少)文本行与行之间的垂直间距的一种方法，但这是查看' line-height '如何工作的一种容易引起误解的简单方法。' line-height '控制' leading '，这是文本行与行之间超出字体大小的额外空间。换句话说，“行高”的值和字体大小之间的区别就是前导。

<Cards cards="line-height" />

When applied to a block-level element, `line-height` defines the `minimum` distance between text baselines within that element. Note that it defines a minimum, not an absolute value, and baselines of text can wind up being pushed further apart than the value of `line-height`. `line-height` does not affect layout for replaced elements, but it still applies to them.

> 当应用于块级元素时，“行高”定义了该元素内文本基线之间的“最小”距离。请注意，它定义了一个最小值，而不是一个绝对值，文本的基线可能会比“行高”的值被推得更远。' line-height '不影响被替换元素的布局，但它仍然适用于它们。

#### Constructing a line

Every element in a line of text generates a `content area`, which is determined by the size of the font. This content area in turn generates an `inline box` that is, in the absence of any other factors, exactly equal to the content area. The leading generated by `line-height` is one of the factors that increases or decreases the height of each inline box.

> 一行文本中的每个元素都会生成一个“内容区域”，该区域由字体的大小决定。这个内容区域反过来又生成一个“内联框”，即在没有任何其他因素的情况下，与内容区域完全相等。“行高”产生的前导是增加或减少每个行内框高度的因素之一。

To determine the leading for a given element, subtract the computed value of `font-size` from the computed value of `line-height`. That value is the total amount of leading. And remember, it can be a negative number. The leading is then divided in half, and each half-leading is applied to the top and bottom of the content area. The result is the inline box for that element.

> 要确定给定元素的前导，请从“行高”的计算值中减去“font-size”的计算值。这个值就是引导的总量。记住，它可以是负数。然后将导语分成两半，每半导语分别应用于内容区域的顶部和底部。结果是该元素的内联框。

As an example, let’s say the `font-size` (and therefore the content area) is 14 pixels tall, and the `line-height` is computed to 18 pixels. The difference (4 pixels) is divided in half, and each half is applied to the top and bottom of the content area. This creates an inline box that is 18 pixels tall, with 2 extra pixels above and below the content area. This sounds like a roundabout way to describe how `line-height` works, but there are excellent reasons for the description.

> 例如，假设“font-size”(即内容区域)是 14 像素高，“line-height”计算为 18 像素。差值(4 个像素)分成两半，每一半应用于内容区域的顶部和底部。这将创建一个 18 像素高的内联框，内容区域上下各有 2 个额外的像素。这听起来像是描述“行高”如何工作的一种迂回的方式，但是这样描述有很好的理由。

Once all of the inline boxes have been generated for a given line of content, they are then considered in the construction of the line box. A line box is exactly as tall as needed to enclose the top of the tallest inline box and the bottom of the lowest inline box. Figure 6-10 shows a diagram of this process.

> 一旦为给定的内容行生成了所有内联框，就会在构建行框时考虑它们。一个线框是完全需要高包围最高的行内框顶部和最低的行内框底部。图 6-10 显示了此过程的关系图。

<Figures figure="6-10">Line box diagram</Figures>

#### Assigning values to line-height

Let’s now consider the possible values of `line-height`. If you use the default value of `normal`, the user agent must calculate the space between lines. Values can vary by user agent, but they’re generally around 1.2 times the size of the font, which makes line boxes taller than the value of `font-size` for a given element.

> 现在让我们考虑' line-height '的可能值。如果使用“normal”的默认值，则用户代理必须计算行与行之间的空间。值可能因用户代理而异，但它们通常是字体大小的 1.2 倍左右，这使得行框比给定元素的“font-size”值要高。

Many values are simple length measures (e.g., `18px` or `2em`), but raw `<number>` values are preferable in many situations. Be aware that even if you use a valid length measurement, such as `4cm`, the browser (or the operating system) may be using an incorrect metric for real-world measurements, so the line height may not show up as exactly four centimeters on your monitor.

> 许多值都是简单的长度度量(例如，' 18px '或' 2em ')，但是原始的' '值在许多情况下更可取。请注意，即使您使用了有效的长度度量，例如“4cm”，浏览器(或操作系统)可能在实际测量中使用了错误的度量，因此在您的显示器上显示的线高可能不是正好 4 厘米。

`em`, `ex`, and percentage values are calculated with respect to the `font-size` of the element. The results of the following CSS and HTML are shown in Figure 6-11:

> `em`、`ex` 和百分比值是根据元素的 `font-size` 计算的。以下 CSS 和 HTML 的结果如图 6-11 所示:

```css
body {
  line-height: 18px;
  font-size: 16px;
}
p.cl1 {
  line-height: 1.5em;
}
p.cl2 {
  font-size: 10px;
  line-height: 150%;
}
p.cl3 {
  line-height: 0.33in;
}
```

```html
<p>
  This paragraph inherits a 'line-height' of 14px from the body, as well as a
  'font-size' of 13px.
</p>
<p class="cl1">
  This paragraph has a 'line-height' of 27px(18 * 1.5), so it will have slightly
  more line-height than usual.
</p>
<p class="cl2">
  This paragraph has a 'line-height' of 15px (10 * 150%), so it will have
  slightly more line-height than usual.
</p>
<p class="cl3">
  This paragraph has a 'line-height' of 0.33in, so it will have slightly more
  line-height than usual.
</p>
```

<Figures figure="6-11">Simple calculations with the line-height property</Figures>

#### Line-height and inheritance

When the `line-height` is inherited by one block-level element from another, things get a bit trickier. `line-height` values inherit from the parent element as computed from the parent, not the child. The results of the following markup are shown in Figure 6-12. It probably wasn’t what the author had in mind:

> 当一个块级元素从另一个块级元素继承' line-height '时，事情就变得有点棘手了。“行高”值从父元素继承，而不是从子元素继承。下面标记的结果如图 6-12 所示。这可能不是作者想要的:

```css
body {
  font-size: 10px;
}
div {
  line-height: 1em;
} /* computes to '10px' */
p {
  font-size: 18px;
}
```

```html
<div>
  <p>
    This paragraph's 'font-size' is 18px, but the inherited 'line-height' value
    is only 10px. This may cause the lines of text to overlap each other by a
    small amount.
  </p>
</div>
```

<Figures figure="6-12">Small line-height, large font-size, slight problem</Figures>

Why are the lines so close together? Because the computed `line-height` value of `10px` was inherited by the paragraph from its parent `div`. One solution to the small `line-height` problem depicted in Figure 6-12 is to set an explicit `line-height` for every element, but that’s not very practical. A better alternative is to specify a number, which actually sets a scaling factor:

> 为什么这两条线这么近?因为计算得到的' line-height '值' 10px '是由该段继承自其父' div '。图 6-12 中描述的小的“行高”问题的一个解决方案是为每个元素设置一个显式的“行高”，但这不是很实用。一个更好的选择是指定一个数字，它实际上设置了一个比例因子:

```css
body {
  font-size: 10px;
}
div {
  line-height: 1;
}
p {
  font-size: 18px;
}
```

When you specify a number, you cause the scaling factor to be an inherited value instead of a computed value. The number will be applied to the element and all of its child elements so that each element has a `line-height` calculated with respect to its own `font-size` (see Figure 6-13):

> 当您指定一个数字时，您将导致缩放因子成为一个继承值，而不是计算值。该数字将应用于元素及其所有子元素，以便每个元素都有一个相对于其“字体大小”计算的“行高”(参见图 6-13):

```css
div {
  line-height: 1.5;
}
p {
  font-size: 18px;
}
```

```html
<div>
  <p>
    This paragraph's 'font-size' is 18px, and since the 'line-height' set for
    the parent div is 1.5, the 'line-height' for this paragraph is 27px (18 *
    1.5).
  </p>
</div>
```

<Figures figure="6-13">Using line-height factors to overcome inheritance problems</Figures>

Though it seems like `line-height` distributes extra space both above and below each line of text, it actually adds (or subtracts) a certain amount from the top and bottom of an inline element’s content area to create an inline box. Assume that the default `font-size` of a paragraph is `12pt` and consider the following:

> 虽然看起来“行高”在每行文本上下都分配了额外的空间，但实际上它从内联元素的内容区域的顶部和底部添加(或减去)了一定量的空间来创建内联框。假设一个段落的默认“字体大小”是“12pt”，并考虑以下情况:

```css
p {
  line-height: 16pt;
}
```

Since the “inherent” line height of 12-point text is 12 points, the preceding rule will place an extra 4 points of space around each line of text in the paragraph. This extra amount is divided in two, with half going above each line and the other half below. You now have 16 points between the baselines, which is an indirect result of how the extra space is apportioned.

> 由于 12 点文本的“固有”行高是 12 点，因此前面的规则将在段落中的每行文本周围额外放置 4 点空间。这个额外的数量被分成两部分，一半在每行上面，另一半在下面。您现在在基线之间有 16 个点，这是如何分配额外空间的间接结果。

If you specify the value `inherit`, then the element will use the computed value for its parent element. This isn’t really any different than allowing the value to inherit naturally, except in terms of specificity and cascade resolution.

> 如果指定值“inherit”，则该元素将使用其父元素的计算值。这与允许值自然地继承没有什么不同，除了在特异性和级联解析方面。

Now that you have a basic grasp of how lines are constructed, let’s talk about “vertically” aligning elements relative to the line box—that is, displacing them along the block direction.

> 现在您已经对如何构造行有了基本的了解，接下来让我们讨论“垂直地”对齐相对于行盒的元素，也就是说，将它们沿着块的方向进行替换。

### 6.2.2 Vertically Aligning Text

If you’ve ever used the elements `sup` and `sub` (the superscript and subscript elements), or used an image with markup such as `<img src="foo.gif" align="middle">`, then you’ve done some rudimentary vertical alignment. In CSS, the `vertical-align` property applies only to inline elements and replaced elements such as images and form inputs. `vertical-align` is not an inherited property.

> 如果您曾经使用过元素' sup '和' sub '(上标和下标元素)，或者使用过带有' gif" align="middle"> '，然后您已经完成了一些基本的垂直对齐。在 CSS 中，“垂直对齐”属性只适用于内联元素和替换元素，如图像和表单输入。“垂直对齐”不是一个继承的属性。

<Tips tips="blue">Because of the property name <code>vertical-align</code>, this section will se the terms “vertical” and “horizontal” to refer to the block and inline directions of the text.</Tips>

<Cards cards="vertical-align" />

`vertical-align` accepts any one of eight keywords, a percentage value, or a length value. The keywords are a mix of the familiar and unfamiliar: `baseline` (the default value), `sub`, `super`, `bottom`, `text-bottom`, `middle`, `top`, and `text-top`. We’ll examine how each keyword works in relation to inline elements.

> `vertical-align` 接受八个关键字中的任何一个，一个百分比值，或一个长度值。关键字是熟悉和不熟悉的混合:“基线”(默认值)、“sub”、“super”、“bottom”、“text-bottom”、“middle”、“top”和“text-top”。我们将研究每个关键字与内联元素之间的关系。

<Tips tips="orange">Remember: <code>vertical-align</code> does <code>not</code> affect the alignment of content within a block-level element. You can, however, use it to affect the vertical alignment of elements within table cells.</Tips>

#### Baseline alignment

`vertical-align: baseline` forces the baseline of an element to align with the baseline of its parent. Browsers, for the most part, do this anyway, since you’d probably expect the bottoms of all text elements in a line to be aligned.

> “垂直对齐:基线”强制元素的基线与其父元素的基线对齐。浏览器通常都会这样做，因为您可能希望一行中所有文本元素的底部都是对齐的。

If a vertically aligned element doesn’t have a baseline—that is, if it’s an image, a form input, or another replaced element—then the bottom of the element is aligned with the baseline of its parent, as Figure 6-14 shows:

> 如果垂直对齐的元素没有基线(也就是说，如果它是一个图像、一个表单输入或另一个替换的元素)，则元素的底部与其父元素的基线对齐，如图 6-14 所示:

```css
img {
  vertical-align: baseline;
}
```

```html
<p>
  The image found in this paragraph <img src="dot.gif" alt="A dot" /> has its
  bottom edge aligned with the baseline of the text in the paragraph.
</p>
```

<Figures figure="6-14">Baseline alignment of an image</Figures>

This alignment rule is important because it causes some web browsers to always put a replaced element’s bottom edge on the baseline, even if there is no other text in the line. For example, let’s say you have an image in a table cell all by itself. The image may actually be on a baseline, but in some browsers, the space below the baseline causes a gap to appear beneath the image. Other browsers will “shrink-wrap” the image with the table cell, and no gap will appear. The gap behavior is correct, despite its lack of appeal to most authors.

> 这个对齐规则非常重要，因为它会导致某些 web 浏览器总是将替换后的元素的底边放在基线上，即使该行中没有其他文本。例如，假设在一个表格单元格中有一个单独的图像。图像实际上可能位于基线上，但在某些浏览器中，基线下的空间会导致图像下方出现间隙。其他浏览器将用表格单元格“收缩包装”图像，不会出现空白。gap 的行为是正确的，尽管它对大多数作者缺乏吸引力。

<Tips tips="blue">See the aged and yet still relevant article “Images, Tables, and Mysterious Gaps” for a more detailed explanation of gap behavior and ways to work around it.</Tips>

#### Superscripting and subscripting

The declaration `vertical-align: sub` causes an element to be subscripted, meaning that its baseline (or bottom, if it’s a replaced element) is lowered with respect to its parent’s baseline. The specification doesn’t define the distance the element is lowered, so it may vary depending on the user agent.

> 声明' vertical-align: sub '导致元素被下标，这意味着它的基线(或者底部，如果它是一个被替换的元素)相对于它的父元素的基线被降低了。规范没有定义降低元素的距离，因此它可能会根据用户代理而变化。

`super` is the opposite of `sub`; it raises the element’s baseline (or bottom of a replaced element) with respect to the parent’s baseline. Again, the distance the text is raised depends on the user agent.

> super 是 sub 的反义词;相对于父元素的基线，它提高了元素的基线(或被替换元素的底部)。同样，文本被提升的距离取决于用户代理。

Note that the values `sub` and `super` do `not` change the element’s font size, so subscripted or superscripted text will not become smaller (or larger). Instead, any text in the sub- or superscripted element should be, by default, the same size as text in the parent element, as illustrated by Figure 6-15:

> 注意，值“sub”和“super”不会改变元素的字体大小，因此下标或上标文本不会变小(或变大)。相反，子元素或上脚本元素中的任何文本在默认情况下都应该与父元素中的文本大小相同，如图 6-15 所示:

```css
span.raise {
  vertical-align: super;
}
span.lower {
  vertical-align: sub;
}
```

```html
<p>
  This paragraph contains <span class="raise">superscripted</span> and
  <span class="lower">subscripted</span> text.
</p>
```

<Figures figure="6-15">Superscript and subscript alignment</Figures>

<Tips tips="blue">If you wish to make super- or subscripted text smaller than the text of its parent element, you can do so using the property <code>font-size</code>.</Tips>

#### Bottom feeding

`vertical-align: bottom` aligns the bottom of the element’s inline box with the bottom of the line box. For example, the following markup results in Figure 6-16:

> 将元素的内联框的底部与行框的底部对齐。例如，下面的标记结果如图 6-16 所示:

```css
.feeder {
  vertical-align: bottom;
}
```

```html
<p>
  This paragraph, as you can see quite clearly, contains a
  <img src="tall.gif" alt="tall" class="feeder" /> image and a
  <img src="short.gif" alt="short" class="feeder" /> image, and then some text
  that is not tall.
</p>
```

<Figures figure="6-16">Bottom alignment</Figures>

The second line of the paragraph in Figure 6-16 contains two inline elements, whose bottom edges are aligned with each other. They’re also below the baseline of the text.

> 图 6-16 中段落的第二行包含两个内联元素，它们的底边彼此对齐。它们也低于文本的基线。

`vertical-align: text-bottom` refers to the bottom of the text in the line. For the purposes of this value, replaced elements, or any other kinds of non-text elements, are ignored. Instead, a “default” text box is considered. This default box is derived from the `font-size` of the parent element. The bottom of the aligned element’s inline box is then aligned with the bottom of the default text box. Thus, given the following markup, you get a result like the one shown in Figure 6-17:

> “垂直对齐:文字底部”指的是一行文字的底部。对于此值，将忽略替换的元素或任何其他类型的非文本元素。取而代之的是一个“默认”文本框。此默认框派生自父元素的“font-size”。对齐元素的内联框的底部然后与默认文本框的底部对齐。因此，给定以下标记，您将得到如图 6-17 所示的结果:

```css
img.tbot {
  vertical-align: text-bottom;
}
```

```html
<p>
  Here: a
  <img src="tall.gif" style="vertical-align: middle;" alt="tall" /> image, and
  then a <img src="short.gif" class="tbot" alt="short" /> image.
</p>
```

<Figures figure="6-17">Text-bottom alignment</Figures>

#### Getting on top

Employing `vertical-align: top` has the opposite effect of `bottom`. Likewise, `vertical-align: text-top` is the reverse of `text-bottom`. Figure 6-18 shows how the following markup would be rendered:

> 使用“垂直对齐:顶部”与“底部”的效果相反。同样，“垂直对齐:文字顶部”是“文字底部”的反义词。图 6-18 显示了如何呈现以下标记:

```css
.up {
  vertical-align: top;
}
.textup {
  vertical-align: text-top;
}
```

```html
<p>
  Here: a <img src="tall.gif" alt="tall image" /> tall image, and then
  <span class="up">some text</span> that's been vertically aligned.
</p>
<p>
  Here: a <img src="tall.gif" class="textup" alt="tall" /> image that's been
  vertically aligned, and then a
  <img src="short.gif" class="textup" alt="short" /> image that's similarly
  aligned.
</p>
```

<Figures figure="6-18">Aligning with the top and text-top of a line</Figures>

The exact position of this alignment will depend on which elements are in the line, how tall they are, and the size of the parent element’s font.

> 这种对齐的确切位置将取决于行中的元素、它们的高度以及父元素的字体大小。

#### In the middle

There’s the value `middle`, which is usually (but not always) applied to images. It does not have the exact effect you might assume given its name. `middle` aligns the middle of an inline element’s box with a point that is `0.5ex` above the baseline of the parent element, where `1ex` is defined relative to the `font-size` for the parent element. Figure 6-19 shows this in more detail.

> 有一个值' middle '，它通常(但不总是)应用于图像。由于它的名字，它并没有你想象的那样的效果。“中间”将行内元素框的中间对齐到父元素基线以上' 0.5ex '处，其中' 1ex '是相对于父元素的' font-size '定义的。图 6-19 更详细地显示了这一点。

<Figures figure="6-19">Precise detail of middle alignment</Figures>

Since most user agents treat `1ex` as one-half em, `middle` usually aligns the vertical midpoint of an element with a point one-quarter em above the parent’s baseline, though this is not a defined distance and so can vary from one user agent to another.

> 由于大多数用户代理将“1ex”视为 1 / 2 em，所以“middle”通常将元素的垂直中点与父元素基线之上的 1 / 4 em 对齐，尽管这不是一个定义的距离，因此不同用户代理之间可能有所不同。

#### Percentages

Percentages don’t let you simulate `align="middle"` for images. Instead, setting a percentage value for `vertical-align` raises or lowers the baseline of the element (or the bottom edge of a replaced element) by the amount declared, with respect to the parent’s baseline. (The percentage you specify is calculated as a percentage of `line-height` for the element, `not` its parent.) Positive percentage values raise the element, and negative values lower it. Depending on how the text is raised or lowered, it can appear to be placed in adjacent lines, as shown in Figure 6-20, so take care when using percentage values:

> 百分比不让您模拟“对齐=“中间”的图像。相反，为“垂直对齐”设置一个百分比值，根据声明的量(相对于父元素的基线)提高或降低元素的基线(或替换元素的底边)。(您指定的百分比是按元素的“行高”百分比计算的，而不是按其父元素的“行高”百分比计算的。)正的百分比值提高元素，负的百分比值降低元素。根据文本的升降方式，它可以显示在相邻的行中，如图 6-20 所示，因此在使用百分比值时要注意:

```css
sub {
  vertical-align: −100%;
}
sup {
  vertical-align: 100%;
}
```

```html
<p>
  We can either <sup>soar to new heights</sup> or, instead,
  <sub>sink into despair...</sub>
</p>
```

<Figures figure="6-20">Percentages and fun effects</Figures>

Let’s consider percentage values in more detail. Assume the following:

> 让我们更详细地考虑百分比值。假设如下:

```html
<div style="font-size: 14px; line-height: 18px;">
  I felt that, if nothing else, I deserved a
  <span style="vertical-align: 50%;">raise</span> for my efforts.
</div>
```

The `50%`-aligned `span` element has its baseline raised nine pixels, which is half of the element’s inherited `line-height` value of `18px`, `not` the seven pixels that would be half the `font-size`.

> “50%”对齐的“span”元素的基线提升了 9 个像素，这是该元素继承的“line-height”值“18px”的一半，而不是“font-size”的一半，即 7 个像素。

#### Length alignment

Finally, let’s consider vertical alignment with a specific length. `vertical-align` is very basic: it shifts an element up or down by the declared distance. Thus, `vertical-align: 5px;` will shift an element upward five pixels from its unaligned placement. Negative length values shift the element downward. This simple form of alignment did not exist in CSS1, but it was added in CSS2.

> 最后，让我们考虑具有特定长度的垂直对齐。“垂直对齐”是非常基本的:它根据声明的距离上下移动一个元素。因此，' vertical-align: 5px; '将把元素从未对齐的位置向上移动 5 个像素。负长度值将元素向下移动。这种简单的对齐形式在 CSS1 中不存在，但在 CSS2 中添加了它。

It’s important to realize that vertically aligned text does not become part of another line, nor does it overlap text in other lines. Consider Figure 6-21, in which some vertically aligned text appears in the middle of a paragraph.

> 必须认识到，垂直对齐的文本不会成为另一行的一部分，也不会与其他行中的文本重叠。考虑图 6-21，其中一些垂直对齐的文本出现在段落中间。

<Figures figure="6-21">Vertical alignments can cause lines to get taller</Figures>

As you can see, any vertically aligned element can affect the height of the line. Recall the description of a line box, which is exactly as tall as necessary to enclose the top of the tallest inline box and the bottom of the lowest inline box. This includes inline boxes that have been shifted up or down by vertical alignment.

> 可以看到，任何垂直对齐的元素都会影响线的高度。回想一下对一个行框的描述，它的高度正好与包围最高行内框的顶部和最低行内框的底部所需的高度相等。这包括通过垂直对齐向上或向下移动的内联框。

## 6.3 Word Spacing and Letter Spacing

Now that we’ve dealt with vertical alignment of inline elements, let’s return to the inline direction for a look at manipulating word and letter spacing. As usual, these properties have some nonintuitive issues.

> 现在，我们已经处理了内联元素的垂直对齐，让我们回到内联方向来查看如何处理单词和字母间距。通常，这些属性有一些不直观的问题。

### 6.3.1 Word Spacing

The `word-spacing` property accepts a positive or negative length. This length is `added` to the standard space between words. In effect, `word-spacing` is used to modify interword spacing. Therefore, the default value of `normal` is the same as setting a value of zero (`0`).

> “单词间隔”属性接受正或负长度。这个长度被“添加”到单词之间的标准空格中。实际上，“词间距”是用来修改词间间距的。因此，“normal”的默认值与设置值 0(“0”)相同。

<Cards cards="word-spacing" />

If you supply a positive length value, then the space between words will increase. Setting a negative value for `word-spacing` brings words closer together:

> 如果您提供的长度值为正，则单词之间的间距将增大。设置“单词间隔”的负值会让单词靠得更近:

```css
p.spread {
  word-spacing: 0.5em;
}
p.tight {
  word-spacing: −0.5em;
}
p.base {
  word-spacing: normal;
}
p.norm {
  word-spacing: 0;
}
```

```html
<p class="spread">
  The spaces between words in this paragraph will be increased by 0.5em.
</p>
<p class="tight">
  The spaces between words in this paragraph will be decreased by 0.5em.
</p>
<p class="base">The spaces between words in this paragraph will be normal.</p>
<p class="norm">The spaces between words in this paragraph will be normal.</p>
```

Manipulating these settings has the effect shown in Figure 6-22.

> 操作这些设置的效果如图 6-22 所示。

<Figures figure="6-22">Changing the space between words</Figures>

So far, I haven’t actually given you a precise definition of “word.” In the simplest CSS terms, a “word” is any string of non-whitespace characters that is surrounded by whitespace of some kind. This definition has no real semantic meaning; it simply assumes that a document contains words, each of which is surrounded by one or more whitespace characters. A CSS-aware user agent cannot be expected to decide what is a valid word in a given language and what isn’t. This definition, such as it is, means `word-spacing` is unlikely to work in any languages that employ pictographs, or non-Roman writing styles. The property allows you to create very unreadable documents, as Figure 6-23 makes clear. Use `word-spacing` with care.

> 到目前为止，我还没有给你一个“词”的精确定义。在最简单的 CSS 术语中，“word”是任何被某种空白包围的非空白字符字符串。这个定义没有真正的语义意义;它只是假设文档包含单词，每个单词由一个或多个空白字符包围。不能指望支持 css 的用户代理来决定什么是给定语言中的有效单词，什么不是。尽管如此，这个定义意味着“单词间隔”在任何使用象形文字或非罗马书写风格的语言中都不太可能奏效。该属性允许您创建非常不可读的文档，如图 6-23 所示。小心使用“单词间隔”。

<Figures figure="6-23">Really wide word spacing</Figures>

### 6.3.2 Letter Spacing

Many of the issues you encounter with `word-spacing` also occur with `letter-spacing`. The only real difference between the two is that `letter-spacing` modifies the space between characters or letters.

> 很多你遇到的“单词间隔”问题也会出现在“字母间隔”上。两者之间唯一真正的区别是“字母间距”修饰字符或字母之间的空间。

<Cards cards="letter-spacing" />

As with the `word-spacing` property, the permitted values of `letter-spacing` include any length. The default keyword is `normal` (making it the same as `letter-spacing: 0`). Any length value you enter will increase or decrease the space between letters by that amount. Figure 6-24 shows the results of the following markup:

> 与“单词间距”属性一样，“字母间距”的允许值包括任何长度。默认的关键字是“normal”(使它与“字母间距:0”相同)。您输入的任何长度值都将增加或减少字母之间的空间。图 6-24 显示了以下标记的结果:

```css
p {
  letter-spacing: 0;
} /* identical to 'normal' */
p.spacious {
  letter-spacing: 0.25em;
}
p.tight {
  letter-spacing: −0.25em;
}
```

```html
<p>The letters in this paragraph are spaced as normal.</p>
<p class="spacious">The letters in this paragraph are spread out a bit.</p>
<p class="tight">The letters in this paragraph are a bit smashed together.</p>
```

<Figures figure="6-24">Various kinds of letter spacing</Figures>

Using `letter-spacing` to increase emphasis is a time-honored technique. You might write the following declaration and get an effect like the one shown in Figure 6-25:

> 使用“字母间距”来增加强调是一种历史悠久的技术。您可以编写以下声明，并获得如图 6-25 所示的效果:

```css
strong {
  letter-spacing: 0.2em;
}
```

```html
<p>
  This paragraph contains <strong>strongly emphasized text</strong> which is
  spread out for extra emphasis.
</p>
```

<Figures figure="6-25">Using letter-spacing to increase emphasis</Figures>

<Tips tips="orange">If a page uses fonts with features like ligatures, and those features are enabled, then altering letter or word spacing can effectively disable them. Browsers will not recalculate ligatures or other joins when letter spacing is altered, for example.</Tips>

### 6.3.3 Spacing and Alignment

The value of `word-spacing` may be influenced by the value of the property `text-align`. If an element is justified, the spaces between letters and words may be altered to fit the text along the full width of the line. This may in turn alter the spacing declared by the author with `word-spacing`. If a length value is assigned to `letter-spacing`, then it cannot be changed by `text-align`; but if the value of `letter-spacing` is `normal`, then inter-character spacing may be changed to justify the text. CSS does not specify how the spacing should be calculated, so user agents fill it in with their own algorithms.

> “单词间隔”的值可能受到“文本对齐”属性值的影响。如果元素是对齐的，字母和单词之间的空格可以改变，以使文本与行宽一致。这可能反过来改变作者用“词间距”声明的间距。如果长度值被赋值为“字母间距”，则不能通过“文本对齐”来更改;但是，如果“字母间距”的值是“正常的”，那么字符之间的间距可能会改变，以调整文本。CSS 没有指定如何计算间距，因此用户代理使用自己的算法填充它。

Note that the computed value is inherited, so child elements with larger or smaller text will have the same letter spacing as their parent element. You cannot define a caling factor for `word-spacing` or `letter-spacing` to be inherited in place of the computed value (as is the case with `line-height`). As a result, you may run into problems such as those shown in Figure 6-26:

> 注意，计算值是继承的，因此文本较大或较小的子元素将具有与其父元素相同的字母间距。您不能定义一个缩放因子来代替计算值来继承“字间距”或“字母间距”(与“行高”的情况相同)。因此，您可能会遇到如图 6-26 所示的问题:

```css
p {
  letter-spacing: 0.25em;
  font-size: 20px;
}
small {
  font-size: 50%;
}
```

```html
<p>
  This spacious paragraph features
  <small>tiny text that is just as spacious</small>, even though the author
  probably wanted the spacing to be in proportion to the size of the text.
</p>
```

<Figures figure="6-26">Inherited letter spacing</Figures>

The only way to achieve letter spacing that’s in proportion to the size of the text is to set it explicitly, as follows:

> 实现字母间距与文本大小成比例的唯一方法是显式地设置它，如下所示:

```css
p {
  letter-spacing: 0.25em;
}
small {
  font-size: 50%;
  letter-spacing: 0.25em;
}
```

## 6.4 Text Transformation

With the alignment properties covered, let’s look at ways to manipulate the capitalization of text using the property `text-transform`.

> 在介绍了对齐属性之后，让我们看看如何使用属性“text-transform”操作文本的大小写。

<Cards cards="text-transform" />

The default value `none` leaves the text alone and uses whatever capitalization exists in the source document. As their names imply, `uppercase` and `lowercase` convert text into all upper- or lowercase characters. Finally, `capitalize` capitalizes only the first letter of each word. Figure 6-27 illustrates each of these settings in a variety of ways:

> 默认值' none '保留文本，并使用源文档中存在的任何大小写。顾名思义，“大写”和“小写”将文本转换为所有大写或小写字符。最后，“首字母大写”只大写每个单词的第一个字母。图 6-27 以多种方式说明了这些设置:

```css
h1 {
  text-transform: capitalize;
}
strong {
  text-transform: uppercase;
}
p.cummings {
  text-transform: lowercase;
}
p.raw {
  text-transform: none;
}
```

```html
<h1>The heading-one at the beginninG</h1>
<p>
  By default, text is displayed in the capitalization it has in the source
  document, but
  <strong>it is possible to change this</strong> using the property
  'text-transform'.
</p>
<p class="cummings">
  For example, one could Create TEXT such as might have been Written by the late
  Poet e.e.cummings.
</p>
<p class="raw">
  If you feel the need to Explicitly Declare the transformation of text to be
  'none', that can be done as well.
</p>
```

<Figures figure="6-27">Various kinds of text transformation</Figures>

Different user agents may have different ways of deciding where words begin and, as a result, which letters are capitalized. For example, the text “heading-one” in the `h1` element, shown in Figure 6-27, could be rendered in one of two ways: “Heading-one” or “Heading-One.” CSS does not say which is correct, so either is possible.

> 不同的用户代理可能有不同的方法来决定单词的开头，因此，哪些字母是大写的。例如，“h1”元素中的文本“heading-one”，如图 6-27 所示，可以以两种方式之一呈现:“heading-one”或“heading-one”。CSS 没有说哪个是正确的，所以两者都是可能的。

You probably also noticed that the last letter in the `h1` element in Figure 6-27 is still uppercase. This is correct: when applying a `text-transform` of `capitalize`, CSS only requires user agents to make sure the first letter of each word is capitalized. They can ignore the rest of the word.

> 您可能还注意到，图 6-27 中的“h1”元素中的最后一个字母仍然是大写的。这是正确的:当应用“大写”的“文本转换”时，CSS 只需要用户代理来确保每个单词的第一个字母是大写的。他们可以忽略单词的其余部分。

As a property, `text-transform` may seem minor, but it’s very useful if you suddenly decide to capitalize all your `h1` elements. Instead of individually changing the content of all your `h1` elements, you can just use `text-transform` to make the change for you:

> 作为一个属性，“text-transform”可能看起来不重要，但是如果您突然决定将所有的“h1”元素大写，那么它就非常有用。你可以使用“text-transform”来代替单独改变你所有“h1”元素的内容:

```css
h1 {
  text-transform: uppercase;
}
```

```html
<h1>This is an H1 element</h1>
```

The advantages of using `text-transform` are twofold. First, you only need to write a single rule to make this change, rather than changing the `h1` itself. Second, if you decide later to switch from all capitals back to initial capitals, the change is even eas‐ ier, as Figure 6-28 shows:

> 使用“文本转换”有两个好处。首先，您只需要编写一个规则来进行此更改，而不是更改“h1”本身。其次，如果你后来决定从所有的大写字母转换回初始大写字母，变化会更大，如图 6-28 所示:

```css
h1 {
  text-transform: capitalize;
}
```

```html
<h1>This is an H1 element</h1>
```

<Figures figure="6-28">Transforming an h1 element</Figures>

Remember that `capitalize` is a simple letter substitution at the beginning of each “word.” It does not mean that common headline-capitalization conventions, such as leaving articles (“a,” “an,” “the”) all lowercase, will be enforced.

> 记住，“大写”是每个“单词”开头的简单字母替换。这并不意味着通用的标题大写惯例，比如冠词(“a”、“an”、“the”)都是小写的，将被强制执行。

## 6.5 Text Decoration

Next we come to `text-decoration`, which is a fascinating property that offers a truckload of interesting behaviors.

> 接下来是“文本装饰”，这是一个非常有趣的特性，它提供了大量有趣的行为。

<Cards cards="text-decoration" />

As you might expect, `underline` causes an element to be underlined, just like the `U` element in ancient HTML. `overline` causes the opposite effect—drawing a line across the top of the text. The value `line-through` draws a line straight through the middle of the text, which is also known as `strikethrough text` and is equivalent to the `S` and `strike` elements in HTML. `blink` causes the text to blink on and off, just like the much-maligned `blink` tag supported by Netscape. Figure 6-29 shows examples of each of these values:

> 如您所料，“下划线”将使元素下划线，就像古代 HTML 中的“U”元素一样。“overline”会产生相反的效果——在文本顶部画一条线。值“line-through”在文本中间绘制一条直线，也称为“strikethrough text”，它相当于 HTML 中的“S”和“strike”元素。“blink”使文本忽明忽暗，就像 Netscape 支持的饱受诟病的“blink”标签一样。图 6-29 展示了这些值的示例:

```css
p.emph {
  text-decoration: underline;
}
p.topper {
  text-decoration: overline;
}
p.old {
  text-decoration: line-through;
}
p.annoy {
  text-decoration: blink;
}
p.plain {
  text-decoration: none;
}
```

<Figures figure="6-29">Various kinds of text decoration</Figures>

<Tips tips="blue">It’s impossible to show the effect of <code>blink</code> in print, but it’s easy enough to imagine (perhaps all too easy). Incidentally, user agents are not required to actually blink <code>blink</code> text; and as of this writing, all known user agents were dropping or had dropped support for the blinking effect. (Internet Explorer never had it.)</Tips>

The value `none` turns off any decoration that might otherwise have been applied to an element. Usually, undecorated text is the default appearance, but not always. For example, links are usually underlined by default. If you want to suppress the underlining of hyperlinks, you can use the following CSS rule to do so:

> 值“none”关闭了任何可能应用于元素的修饰。通常，未修饰的文本是默认的外观，但并非总是如此。例如，链接通常在默认情况下加下划线。如果你想隐藏超链接的下划线，你可以使用以下 CSS 规则:

```css
a {
  text-decoration: none;
}
```

If you explicitly turn off link underlining with this sort of rule, the only visual difference between the anchors and normal text will be their color (at least by default, though there’s no ironclad guarantee that there will be a difference in their colors).

> 如果您使用这种规则显式地关闭了链接下划线，那么锚点和普通文本之间的唯一视觉差异将是它们的颜色(至少在默认情况下是这样，尽管不能保证它们的颜色会有差异)。

<Tips tips="blue">Bear in mind that many users are annoyed when they realize you’ve turned off link underlining. It’s a matter of opinion, so let your own tastes be your guide, but remember: if your link colors aren’t sufficiently different from normal text, users may have a hard time find‐ing hyperlinks in your documents, particularly users with one form or another of color blindness.</Tips>

You can also combine decorations in a single rule. If you want all hyperlinks to be both underlined and overlined, the rule is:

> 您还可以在单个规则中组合装饰。如果你想让所有的超链接都下划线和下划线，规则是:

```css
a:link,
a:visited {
  text-decoration: underline overline;
}
```

Be careful, though: if you have two different decorations matched to the same element, the value of the rule that wins out will completely replace the value of the loser. Consider:

> 但是要小心:如果有两个不同的装饰物匹配到相同的元素，则胜出规则的值将完全取代失败者的值。考虑:

```css
h2.stricken {
  text-decoration: line-through;
}
h2 {
  text-decoration: underline overline;
}
```

Given these rules, any `h2` element with a class of `stricken` will have only a linethrough decoration. The underline and overline decorations are lost, since shorthand values replace one another instead of accumulating.

> 根据这些规则，任何带有“”类的“h2”元素将只有一个贯穿装饰。由于简写值代替了其他值而不是累加，所以下划线和上划线修饰丢失了。

### 6.5.1 Weird Decorations

Now, let’s look into the unusual side of `text-decoration`. The first oddity is that `text-decoration` is `not` inherited. No inheritance implies that any decoration lines drawn with the text—under, over, or through it—will be the same color as the parent element. This is true even if the descendant elements are a different color, as depicted in Figure 6-30:

> 现在，让我们来看看“文字装饰”不寻常的一面。第一个奇怪之处是“文本装饰”不是继承而来的。没有继承意味着用文本绘制的任何装饰线—下、上或通过—将与父元素相同的颜色。即使子代元素是不同的颜色也是如此，如图 6-30 所示:

```css
p {
  text-decoration: underline;
  color: black;
}
strong {
  color: gray;
}
```

```html
<p>
  This paragraph, which is black and has a black underline, also contains
  <strong>strongly emphasized text</strong> which has the black underline
  beneath it as well.
</p>
```

<Figures figure="6-30">Color consistency in underlines</Figures>

Why is this so? Because the value of `text-decoration` is not inherited, the `strong` element assumes a default value of `none`. Therefore, the `strong` element has `no` underline. Now, there is very clearly a line under the `strong` element, so it seems silly to say that it has none. Nevertheless, it doesn’t. What you see under the `strong` element is the paragraph’s underline, which is effectively “spanning” the `strong` element. You can see it more clearly if you alter the styles for the boldface element, like this:

> 为什么会这样?因为“text-decoration”的值不是继承的，所以“strong”元素的默认值是“none”。因此，“强”元素有“no”下划线。现在，在“强”元素下面有一条非常明显的线，所以说它没有是很愚蠢的。然而,它不。你在“强”元素下面看到的是段落的下划线，它有效地“跨越”了“强”元素。如果你改变黑体元素的样式，你可以看得更清楚，就像这样:

```css
p {
  text-decoration: underline;
  color: black;
}
strong {
  color: gray;
  text-decoration: none;
}
```

```html
<p>
  This paragraph, which is black and has a black underline, also contains
  <strong>strongly emphasized text</strong> which has the black underline
  beneath it as well.
</p>
```

The result is identical to the one shown in Figure 6-30, since all you’ve done is to explicitly declare what was already the case. In other words, there is no way to turn off underlining (or overlining or a line-through) generated by a parent element.

> 结果与图 6-30 所示的相同，因为您所做的就是显式地声明已经发生的情况。换句话说，无法关闭父元素生成的下划线(或下划线或换行)。

When `text-decoration` is combined with `vertical-align`, even stranger things can happen. Figure 6-31 shows one of these oddities. Since the `sup` element has no decoration of its own, but it is elevated within an overlined element, the overline cuts through the middle of the `sup` element:

> 当“文字装饰”与“垂直对齐”相结合时，更奇怪的事情也会发生。图 6-31 显示了其中一个奇怪的地方。由于“sup”元素本身没有装饰，但是它在一个覆盖的元素中被提升了，所以 overline 从“sup”元素的中间穿过:

```css
p {
  text-decoration: overline;
  font-size: 12pt;
}
sup {
  vertical-align: 50%;
  font-size: 12pt;
}
```

<Figures figure="6-31">Correct, although strange, decorative behavior</Figures>

By now you may be vowing never to use text decorations because of all the problems they could create. In fact, I’ve given you the simplest possible outcomes since we’ve explored only the way things `should` work according to the specification. In reality, some web browsers do turn off underlining in child elements, even though they aren’t supposed to. The reason browsers violate the specification is author expectations. Consider this markup:

> 到目前为止，您可能已经发誓永远不会使用文本装饰，因为它们可能会造成所有的问题。事实上，我已经给出了最简单的可能结果，因为我们只研究了事情按照规范“应该”工作的方式。实际上，一些 web 浏览器确实关闭了子元素中的下划线，尽管它们不应该这样做。浏览器违反规范的原因是作者的期望。考虑一下这个标记:

```css
p {
  text-decoration: underline;
  color: black;
}
strong {
  color: silver;
  text-decoration: none;
}
```

```html
<p>
  This paragraph, which is black and has a black underline, also contains
  <strong>boldfaced text</strong> which does not have black underline beneath
  it.
</p>
```

Figure 6-32 shows the display in a web browser that has switched off the underlining for the strong element.

> 图 6-32 显示了关闭了 strong 元素下划线的 web 浏览器中的显示。

<Figures figure="6-32">How some browsers really behave</Figures>

The caveat here is that many browsers `do` follow the specification, and future versions of existing browsers (or any other user agents) might one day follow the specification precisely. If you depend on using `none` to suppress decorations, it’s important to realize that it may come back to haunt you in the future, or even cause you problems in the present. Then again, future versions of CSS may include the means to turn off decorations without using `none` incorrectly, so maybe there’s hope.

> 这里的警告是，许多浏览器“确实”遵循规范，现有浏览器(或任何其他用户代理)的未来版本可能有一天会精确地遵循规范。如果你依赖于使用“无”来压制装饰，那么重要的是要意识到它可能会在未来困扰你，甚至在现在给你带来麻烦。此外，未来的 CSS 版本可能会包括关闭装饰而不正确使用“none”的方法，所以也许还有希望。

There is a way to change the color of a decoration without violating the specification. As you’ll recall, setting a text decoration on an element means that the entire element has the same color decoration, even if there are child elements of different colors. To match the decoration color with an element, you must explicitly declare its decoration, as follows:

> 有一种方法可以在不违反规范的情况下改变装饰的颜色。您可能还记得，在元素上设置文本装饰意味着整个元素具有相同的颜色装饰，即使有不同颜色的子元素。要将装饰颜色与元素匹配，必须显式声明其装饰，如下所示:

```css
p {
  text-decoration: underline;
  color: black;
}
strong {
  color: silver;
  text-decoration: underline;
}
```

```html
<p>
  This paragraph, which is black and has a black underline, also contains
  <strong>strongly emphasized text</strong> which has the black underline
  beneath it as well, but whose gray underline overlays the black underline of
  its parent.
</p>
```

In Figure 6-33, the `strong` element is set to be gray and to have an underline. The gray underline visually “overwrites” the parent’s black underline, so the decoration’s color matches the color of the `strong` element.

> 在图 6-33 中，“strong”元素被设置为灰色并带有下划线。灰色下划线在视觉上“覆盖”了父元素的黑色下划线，因此装饰的颜色与“强”元素的颜色相匹配。

<Figures figure="6-33">Overcoming the default behavior of underlines</Figures>

## 6.6 Text Rendering

A recent addition to CSS is `text-rendering`, which is actually an SVG property that is nevertheless treated as CSS by supporting user agents. It lets authors indicate what the user agent should prioritize when displaying text.

> CSS 的一个新特性是“文本呈现”，它实际上是一个 SVG 属性，但是支持用户代理的人却将其视为 CSS。它允许作者在显示文本时指出用户代理应该优先处理什么。

<Cards cards="text-rendering" />

The values `optimizeSpeed` and `optimizeLegibility` are relatively self-explanatory, indicating that drawing speed should be favored over legibility features like kerning and ligatures (for `optimizeSpeed`) or vice versa (for `optimizeLegibility`).

> ' optimizeSpeed '和' optimizele'这两个值相对来说是不言自明的，这表明绘图速度应该优先于字距和连接等易读特性(对于' optimizeSpeed ')，反之亦然(对于' optimizele')。

The precise legibility features that are used with `optimizeLegibility` are not explicitly defined, and the text rendering often depends on the operating system on which the user agent is running, so the exact results may vary. Figure 6-34 shows text optimized for speed, and then optimized for legibility.

> “optimizele”中使用的精确易读特性没有明确定义，文本呈现通常取决于用户代理运行的操作系统，因此准确的结果可能会有所不同。图 6-34 显示了经过速度优化和易读性优化的文本。

<Figures figure="6-34">Different optimizations</Figures>

As you can see in Figure 6-34, the differences between the two optimizations are objectively rather small, but they can have a noticeable impact on readability.

> 正如您在图 6-34 中所看到的，这两种优化之间的差异在客观上非常小，但是它们对可读性有显著的影响。

<Tips tips="blue">Some user agents will always optimize for legibility, even when optimizing for speed. This is likely an effect of rendering speeds having gotten so fast in the past few years.</Tips>

The value `geometricPrecision`, on the other hand, directs the user agent to draw the text as precisely as possible, such that it could be scaled up or down with no loss of fidelity. You might think that this is always the case, but not so. Some fonts change kerning or ligature effects at different text sizes, for example, providing more kerning space at smaller sizes and tightening up the kerning space as the size is increased. With `geometricPrecision`, those hints are ignored as the text size changes. If it helps, think of it as the user agent drawing the text as though all the text is a series of SVG paths, not font glyphs.

> 另一方面，值' geometricPrecision '指示用户代理尽可能精确地绘制文本，这样就可以在不损失保真度的情况下按比例放大或缩小文本。你可能认为情况总是如此，但事实并非如此。有些字体会在不同的文本大小时改变字距或连接效果，例如，在较小的字体大小时提供更多的字距空间，并随着字体大小的增加而收紧字距空间。使用“geometricPrecision”，当文本大小改变时，这些提示将被忽略。如果有帮助，可以将其视为绘制文本的用户代理，就好像所有文本都是一系列 SVG 路径，而不是字体符号。

Even by the usual standard of web standards, the value `auto` is pretty vaguely defined in SVG:

> 即使按照通常的 web 标准，“auto”的值在 SVG 中也定义得很模糊:

the user agent shall make appropriate tradeoffs to balance speed, legibility and geometric precision, but with legibility given more importance than speed and geometric precision.

> 用户代理应在速度、易读性和几何精度之间做出适当的权衡，但易读性比速度和几何精度更重要。

That’s it: user agents get to do what they think is appropriate, leaning towards legibility.

> 就是这样:用户代理可以做他们认为合适的事情，倾向于易读性。

## 6.7 Text Shadows

Sometimes, you just really need your text to cast a shadow. That’s where `text-shadow` comes in. The syntax might look a little wacky at first, but it should become clear enough with just a little practice.

> 有时候，你真的需要你的文字来投下阴影。这就是“文本阴影”发挥作用的地方。语法一开始可能看起来有点古怪，但只要稍加练习就会变得足够清晰。

<Cards cards="text-shadow" />

The default is to not have a drop shadow for text. Otherwise, it’s possible to define one or more shadows. Each shadow is defined by an optional color and three length values, the last of which is also optional.

> 默认情况下，文本没有投影。否则，可以定义一个或多个阴影。每个阴影由一个可选的颜色和三个长度值定义，最后一个也是可选的。

The color sets the shadow’s color so it’s possible to define green, purple, or even white shadows. If the color is omitted, the shadow will be the same color as the text.

> 颜色设置阴影的颜色，因此可以定义绿色、紫色甚至白色的阴影。如果省略颜色，阴影将与文本的颜色相同。

The first two length values determine the offset distance of the shadow from the text; the first is the horizontal offset and the second is the vertical offset. To define a solid, un-blurred green shadow offset five pixels to the right and half an em down from the text, as shown in Figure 6-35, you would write:

> 前两个长度值决定阴影到文本的偏移距离;第一个是水平偏移，第二个是垂直偏移。要定义一个实体的、未模糊的绿色阴影，从文本向右偏移 5 个像素，向下半个 em，如图 6-35 所示，您可以这样写:

```css
text-shadow: green 5px 0.5em;
```

Negative lengths cause the shadow to be offset to the left and upward from the original text. The following, also shown in Figure 6-35, places a light blue shadow five pixels to the left and half an em above the text:

> 负长度使阴影从原始文本向左向上偏移。如下图 6-35 所示，在文本左侧 5 个像素处放置一个淡蓝色阴影，在文本上方放置半个 em:

```css
text-shadow: rgb(128, 128, 255) −5px −0.5em;
```

<Figures figure="6-35">Simple shadows</Figures>

The optional third length value defines a blur radius for the shadow. The `blur radius` is defined as the distance from the shadow’s outline to the edge of the blurring effect. A radius of two pixels would result in blurring that fills the space between the shadow’s outline and the edge of the blurring. The exact blurring method is not defined, so different user agents might employ different effects. As an example, the following styles are rendered as shown in Figure 6-36:

> 可选的第三个长度值定义了阴影的模糊半径。“模糊半径”定义为从阴影轮廓到模糊效果边缘的距离。两个像素的半径将导致模糊，填充阴影轮廓和模糊边缘之间的空间。精确的模糊方法没有定义，因此不同的用户代理可能使用不同的效果。例如，如下图 6-36 所示的样式:

```css
p.cl1 {
  color: black;
  text-shadow: gray 2px 2px 4px;
}
p.cl2 {
  color: white;
  text-shadow: 0 0 4px black;
}
p.cl3 {
  color: black;
  text-shadow: 1em 0.5em 5px red, −0.5em −1em hsla(100, 75%, 25%, 0.33);
}
```

<Figures figure="6-36">Dropping shadows all over</Figures>

<Tips tips="blue">Note that large numbers of text shadows, or text shadows with very large blur values, can create performance slowdowns, particularly in low-power and CPU-constrained situations such as mobile devices. Authors are advised to test thoroughly before deploying public designs that use text shadows.</Tips>

## 6.8 Handling Whitespace

Now that we’ve covered a variety of ways to style the text, let’s talk about the property `white-space`, which affects the user agent’s handling of space, newline, and tab characters within the document source.

> 现在我们已经介绍了文本样式的各种方法，接下来讨论属性“空白”，它影响用户代理对文档源中的空格、换行符和制表符的处理。

<Cards cards="white-space" />

Using this property, you can affect how a browser treats the whitespace between words and lines of text. To a certain extent, default XHTML handling already does this: it collapses any whitespace down to a single space. So given the following markup, the rendering in a web browser would show only one space between each word and ignore the line-feed in the elements:

> 使用此属性，您可以影响浏览器如何处理单词和文本行之间的空白。在某种程度上，默认的 XHTML 处理已经做到了这一点:它将任何空白压缩为单个空间。因此，对于以下标记，web 浏览器中的呈现将在每个单词之间只显示一个空格，而忽略元素中的换行:

```html
<p>This paragraph has many spaces in it.</p>
```

You can explicitly set this default behavior with the following declaration:

> 您可以显式地设置这一默认行为与以下声明:

```css
p {
  white-space: normal;
}
```

This rule tells the browser to do as browsers have always done: discard extra whitespace. Given this value, line-feed characters (carriage returns) are converted into spaces, and any sequence of more than one space in a row is converted to a single space.

> 这个规则告诉浏览器做浏览器一直做的事情:丢弃多余的空白。给定此值，换行符(回车)将转换为空格，行中多个空格的任何序列将转换为单个空格。

Should you set `white-space` to `pre`, however, the whitespace in an affected element is treated as though the elements were XHTML `pre` elements; whitespace is `not` ignored, as shown in Figure 6-37:

> 然而，如果将“空白”设置为“pre”，则受影响元素中的空白将被视为 XHTML“pre”元素;空格不会被忽略，如图 6-37 所示:

```css
p {
  white-space: pre;
}
```

```html
<p>This paragraph has many spaces in it.</p>
```

<Figures figure="6-37">Honoring the spaces in markup</Figures>

With a `white-space` value of `pre`, the browser will pay attention to extra spaces and even carriage returns. In this respect, and in this respect alone, any element can be made to act like a `pre` element.

> 如果“空白”的值是“pre”，浏览器就会注意额外的空格，甚至是回车符。在这方面，仅在这方面，任何元素都可以充当“pre”元素。

The opposite value is `nowrap`, which prevents text from wrapping within an element, except wherever you use a `br` element. Using `nowrap` in CSS is much like setting a table cell not to wrap in HTML 4 with `<td nowrap>`, except the `white-space` value can be applied to any element. The effects of the following markup are shown in Figure 6-38:

> 相反的值是“nowrap”，它可以防止文本在元素中换行，除非使用“br”元素。在 CSS 中使用‘nowrap’很像在 HTML 4 中设置一个不带‘’的表格单元格，只是‘空白’值可以应用于任何元素。以下标记的效果如图 6-38 所示:

```html
<p style="white-space: nowrap;">
  This paragraph is not allowed to wrap, which means that the only way to end a
  line is to insert a line-break element. If no such element is inserted, then
  the line will go forever, forcing the user to scroll horizontally to read
  whatever can't be initially displayed <br />in the browser window.
</p>
```

<Figures figure="6-38">Suppressing line wrapping with the white-space property</Figures>

You can actually use `white-space` to replace the `nowrap` attribute on table cells:

```css
td {
  white-space: nowrap;
}
```

```html
<table>
  <tr>
    <td>The contents of this cell are not wrapped.</td>
    <td>Neither are the contents of this cell.</td>
    <td>Nor this one, or any after it, or any other cell in this table.</td>
    <td>CSS prevents any wrapping from happening.</td>
  </tr>
</table>
```

CSS 2.1 introduced the values `pre-wrap` and `pre-line`, which were absent in earlier versions of CSS. The effect of these values is to allow authors to better control whitespace handling.

> CSS 2.1 引入了“pre-wrap”和“pre-line”值，这两个值在早期的 CSS 版本中是不存在的。这些值的作用是允许作者更好地控制空白处理。

If an element is set to `pre-wrap`, then text within that element has whitespace sequences preserved, but text lines are wrapped normally. With this value, line-breaks in the source and those that are generated are also honored. `pre-line` is the opposite of `pre-wrap` and causes whitespace sequences to collapse as in normal text but honors new lines. For example, consider the following markup, which is illustrated in Figure 6-39:

> 如果一个元素被设置为“预包装”，那么该元素中的文本将保留空白序列，但是文本行通常被包装。有了这个值，源代码中的断行符和生成的断行符也将得到使用。“pre-line”是“pre-wrap”的反义词，它会导致空格序列崩溃，就像普通文本一样，但是会增加新行。例如，考虑下面的标记，如图 6-39 所示:

```html
<p style="white-space: pre-wrap;">
  This paragraph has a great many s p a c e s within its textual content, but
  their preservation will not prevent line wrapping or line breaking.
</p>
<p style="white-space: pre-line;">
  This paragraph has a great many s p a c e s within its textual content, but
  their collapse will not prevent line wrapping or line breaking.
</p>
```

<Figures figure="6-39">Two different ways to handle whitespace</Figures>

Table 6-1 summarizes the behaviors of white-space properties.

| Value    | Whitespace | Line feeds | Auto line wrapping |
| -------- | ---------- | ---------- | ------------------ |
| pre-line | Collapsed  | Honored    | Allowed            |
| normal   | Collapsed  | Ignored    | Allowed            |
| nowrap   | Collapsed  | Ignored    | Prevented          |
| pre      | Preserved  | Honored    | Prevented          |
| pre-wrap | Preserved  | Honored    | Allowed            |

### 6.8.1 Setting Tab Sizes

Since whitespace is preserved in some values of `white-space`, it stands to reason that tabs (i.e., Unicode code point 0009) will be displayed as, well, tabs. But how many spaces should each tab equal? That’s where `tab-size` comes in.

> 由于空白保留在“空白空间”的某些值中，所以制表符(即， Unicode 编码点 0009)将显示为制表符。但是每个选项卡应该等于多少空格呢?这就是“tab-size”的用武之地。

<Cards cards="tab-size" />

By default, any tab character will be treated the same as eight spaces in a row, but you can alter that by using a different integer value. Thus, `tab-size: 4` will cause each tab to be rendered the same as if it were four spaces in a row.

> 默认情况下，任何制表符都将被视为一行中的八个空格，但是您可以通过使用不同的整数值来改变这一点。因此，“tab-size: 4”将使每个选项卡呈现为与一行中的四个空格相同的效果。

If a length value is supplied, then each tab is rendered using that length. For example, `tab-size: 10px` will cause a sequence of three tabs to be rendered as 30 pixels of whitespace. The effects of the following rules is illustrated in Figure 6-40.

> 如果提供了长度值，则使用该长度呈现每个选项卡。例如，“tab-size: 10px”将导致三个标签的序列呈现为 30 像素的空白。下面这些规则的效果如图 6-40 所示。

<Figures figure="6-40">Differing tab lengths</Figures>

Note that `tab-size` is effectively ignored when the value of `white-space` causes whitespace to be collapsed (see Table 6-1). The value will still be computed in such cases, but there will be no visible effect no matter how many tabs appear in the source.

> 请注意，当“空白空间”的值导致空格折叠时，“tab-size”实际上被忽略(参见表 6-1)。在这种情况下，值仍然会被计算，但是无论源中出现多少个选项卡，都不会有可见的效果。

<Tips tips="blue">Currently, <code>tab-size</code> is supported in WebKit and Gecko (as <code>–moztab-size</code>). In both cases, only integer values are supported, not length values.</Tips>

## 6.9 Wrapping and Hyphenation

Hyphens can be very useful in situations where there are long words and short line lengths, such as blog posts on mobile devices and portions of `The Economist`. Authors can always insert their own hyphenation hints using the Unicode character U+00AD SOFT HYPHEN (or, in HTML, `&shy;`), but CSS also offers a way to enable hyphenation without littering up the document with hints.

> 连字符在长单词和短行长度的情况下非常有用，比如移动设备上的博客文章和《经济学人》的部分内容。作者总是可以使用 Unicode 字符 U+00AD 软连字符(或者，在 HTML 中，' - ')插入自己的连字符提示，但是 CSS 也提供了一种方法来支持连字符，而不用在文档中使用提示。

<Cards cards="hyphens" />

With the default value of `manual`, hyphens are only inserted where there are manually-inserted hyphenation markers in the document, such as U+00AD or `&shy`;. Otherwise, no hyphenation occurs. The value `none`, on the other hand, suppresses any hyphenation, even if manual break markers are present; thus, U+00AD and `&shy;` are ignored.

> 默认值为“manual”时，只有在文档中有手动插入的连字符标记的地方才会插入连字符，比如 U+00AD 或“­”;。否则，不会出现断字。另一方面，值“none”则抑制任何连字符，即使存在手动中断标记;因此，U+00AD 和' - '被忽略。

The far more interesting (and potentially inconsistent) value is `auto`, which permits the browser to insert hyphens and break words at “appropriate” places inside words, even where no manually inserted hyphenation breaks exist. This leads to interesting questions like what constitutes a “word” and under what circumstances it is appropriate to hyphenate a word, both of which are highly language-dependent. User agents are supposed to prefer manually inserted hyphen breaks to automatically determined breaks, but there are no guarantees. An illustration of hyphenation, or the suppression thereof, in the following example is shown in Figure 6-41:

> 更有趣(而且可能不一致)的值是“auto”，它允许浏览器在单词内部的“适当”位置插入连字符并中断单词，即使在没有手动插入连字符中断的地方也是如此。这就引出了一些有趣的问题，比如什么构成了一个“单词”，在什么情况下用连字符连接单词是合适的，这两个问题都与语言高度相关。用户代理应该更喜欢手动插入的连字符分隔符，而不是自动确定的分隔符，但是没有保证。下面的例子中，断字或其抑制的说明如图 6-41 所示:

```css
.cl01 {
  hyphens: auto;
}
.cl02 {
  hyphens: manual;
}
.cl03 {
  hyphens: none;
}
```

```html
<p class="cl01">
  Supercalifragilisticexpialidocious antidisestablishmentarian ism.
</p>
<p class="cl02">
  Supercalifragilisticexpialidocious antidisestablishmentarian ism.
</p>
<p class="cl02">
  Super&#xad;cali&#xad;fragi&#xad;listic&#xad;expi&#xad;ali&#xad; docious
  anti&#xad;dis&#xad;establish&#xad;ment&#xad;arian&#xad;ism.
</p>
<p class="cl03">
  Super&#xad;cali&#xad;fragi&#xad;listic&#xad;expi&#xad;ali&#xad; docious
  anti&#xad;dis&#xad;establish&#xad;ment&#xad;arian&#xad;ism.
</p>
```

<Figures figure="6-41">Hyphenation results</Figures>

Because hyphenation is so language-dependent, and because the CSS specification does not define precise (or even vague) rules regarding how user agents should carry out hyphenation, there is every chance that hyphenation will be different from one browser to the next.

> 因为连字符依赖于语言，而且 CSS 规范没有定义关于用户代理应该如何执行连字符的精确(甚至模糊)规则，所以很有可能连字符在不同的浏览器之间是不同的。

Furthermore, if you do choose to hyphenate, be careful about the elements to which you apply the hyphenation. `hyphens` is an inherited property, so declaring `body {hyphens: auto;}` will apply hyphenation to everything in your document—including textareas, code samples, block quotes, and so on. Blocking automatic hyphenation at the level of those elements is probably a good idea, using rules something like this:

> 此外，如果您选择使用断字，请小心使用断字的元素。“连字符”是一个继承属性，因此声明“body{连字符:auto;}”将对文档中的所有内容应用连字符——包括文本区域、代码示例、块引号等等。在这些元素级别上阻止自动断字可能是一个好主意，使用类似这样的规则:

```css
body {hyphens: auto;}
code, var, kbd, samp, tt, dir, listing, plaintext, xmp, abbr, acronym,
blockquote, q, textarea, input, option {hyphens: manual;}
.
```

It’s probably obvious why suppressing hyphenation in code samples and code blocks is desirable, especially in languages that use hyphens in things like property and value names. (Ahem.) Similar logic holds for keyboard input text—you definitely don’t want a stray dash getting into your Unix command-line examples! And so on down the line. If you decide that you want to hyphenate some of these elements, just remove them from the selector. (It can be kind of fun to watch the text you’re typing into a textarea get auto-hyphenated as you type it.)

> 在代码示例和代码块中禁用连字符的原因可能很明显，尤其是在属性和值名称中使用连字符的语言中。(嗯)。类似的逻辑也适用于键盘输入文本——您肯定不希望在您的 Unix 命令行示例中出现任何错误!以此类推。如果您决定要对其中一些元素进行断字，只需将它们从选择器中删除即可。(看着你在文本框中输入的文字在你输入时自动连字符也是一种乐趣。)

<Tips tips="orange">As of late 2017, <code>hyphens</code> was supported by all major desktop browsers except Chrome/Blink, and required vendor prefixes in Safari and Edge. As noted, such support is always languagedependent.</Tips>

Hyphens can be suppressed by the effects of other properties, such as <code>word-break</code>, which affects how soft wrapping of text is calculated in various languages.

> 连字符可以被其他属性的影响所抑制，例如 word-break，这影响了在各种语言中如何计算文本的软包装。

<Cards cards="word-break" />

When a run of text is too long to fit into a single line, it is `soft wrapped`. This is in contrast to `hard wraps`, which are things like line-feed characters and `<br>` elements. Where the text is soft wrapped is determined by the user agent (or the OS it uses), but `word-break` lets authors influence its decision-making.

> 当一段文字太长，无法容纳一行时，它就被“软包装”了。这与“硬包装”形成对比，后者类似于换行字符和“”元素。文本是否软包装是由用户代理(或其使用的操作系统)决定的，但是“word-break”允许作者影响其决策。

The default value of `normal` means that text should be wrapped like it always has been. In practical terms, this means that text is broken between words, though the definition of a word varies by language. In Latin-derived languages like English, this is almost always a space between letter sequences (e.g., words). In ideographic languages like Japanese, each symbol is a word, so breaks can occur between any two symbols. In other CJK languages, though, the soft-wrap points may be limited to appear between sequences of symbols that are not space-separated.

> “正常”的默认值意味着文本应该像往常一样被包装。在实践中，这意味着文本在单词之间被分割，尽管单词的定义因语言而异。在像英语这样源自拉丁语的语言中，这几乎总是字母序列(例如单词)之间的空格。在像日语这样的表意文字语言中，每个符号都是一个单词，因此任何两个符号之间都可能发生中断。然而，在其他 CJK 语言中，软包点可能被限制出现在不以空格分隔的符号序列之间。

Again, that’s all by default, and is the way browsers have handled text for years. If you apply the value `break-all`, then soft wrapping can (and will) occur between any two characters, even if they are in the middle of a word. With this value, no hyphens are shown, even if the soft wrapping occurs at a hyphenation point (see `hyphens`, earlier). Note that values of the `line-break` property (described next) can affect the behavior of `break-all` in CJK text.

> 同样，这些都是默认的，也是浏览器多年来处理文本的方式。如果应用“break-all”值，则软换行可以(也将)发生在任何两个字符之间，即使它们位于单词中间。使用此值时，不显示连字符，即使软包装发生在连字符处(请参阅前面的“连字符”)。注意，' line-break '属性的值(下面将进行描述)会影响 CJK 文本中' break-all '的行为。

`keep-all`, on the other hand, suppresses soft wrapping between characters, even in CJK languages where each symbol is a word. Thus, in Japanese, a sequence of symbols with no whitespace will not be soft wrapped, even if this means the text line will exceed the length of its element. (This behavior is similar to `white-space: pre`.) Figure 6-42 shows a few examples of word-break values, and Table 6-2 summarizes the effects of each value.

> 另一方面，“keep-all”抑制了字符之间的软包装，即使在 CJK 语言中，每个符号都是一个单词。因此，在日语中，没有空格的符号序列不会被软包装，即使这意味着文本行将超过其元素的长度。(这种行为类似于“空白:pre”。)图 6-42 显示了一些分词值的示例，表 6-2 总结了每个值的影响。

<Figures figure="6-42">Altering word-breaking behavior</Figures>

Table 6-2. Word-breaking behavior

| Value     | Non-CJK             | CJK                 | Hyphenation permitted |
| --------- | ------------------- | ------------------- | --------------------- |
| normal    | As usual            | As usual            | Yes                   |
| break-all | After any character | After any character | No                    |
| keep-all  | As usual            | Around sequences    | Yes                   |

If your interests run to CJK text, then in addition to `word-break` you will also want to get to know `line-break`.

> 如果你对 CJK 文本感兴趣，那么除了“word break”之外，你还需要了解“line-break”。

<Cards cards="line-break" />

As we just saw, `word-break` can affect how lines of text are soft wrapped in CJK text. The `line-break` property also affects such soft wrapping, specifically how wrapping is handled around CJK-specific symbols and around non-CJK punctuation (such as exclamation points, hyphens, and ellipses) that appears in text declared to be CJK.

> 正如我们刚才看到的，“word-break”会影响 CJK 文本中文本行被软包装的方式。“换行”属性也会影响这种软包装，特别是在声明为 CJK 的文本中出现的特定于 CJK 的符号和非 CJK 标点符号(如感叹号、连字符和省略号)周围如何处理换行。

In other words, `line-break` applies to certain CJK characters all the time, regardless of the content’s declared language. If you throw some CJK characters into a paragraph of English text, `line-break` will still apply to them, but not to anything else in the text. Conversely, if you declare content to be in a CJK language, `line-break` will continue to apply to those CJK characters `plus` a number of non-CJK characters within the CJK text. These include punctuation marks, currency symbols, and a few other symbols.

> 换句话说，无论内容的声明语言是什么，“断行”始终适用于某些 CJK 字符。如果您将一些 CJK 字符放入一段英文文本中，“断行”仍然适用于它们，但不适用于文本中的任何其他内容。相反，如果您声明内容是 CJK 语言的，则“断行”将继续应用于那些 CJK 字符“加上”CJK 文本中的许多非 CJK 字符。这些符号包括标点符号、货币符号和其他一些符号。

There is no authoritative list of which characters are affected and which are not, but the specification provides a list of recommended symbols and behaviors around those symbols.

> 对于哪些字符受影响，哪些不受影响，并没有权威的列表，但是规范提供了关于这些符号的推荐符号和行为的列表。

The default value `auto` allows user agents to soft wrap text as they like, and more importantly lets UAs vary the line breaking they do based on the situation. For example, the UA can use looser line-breaking rules for short lines of text and stricter rules for long lines. In effect, `auto` allows the user agent to switch between the `loose`, `normal`, and `strict` values as needed, possibly even on a line-by-line basis within a single element.

> 默认值“auto”允许用户代理随心所欲地对文本进行软包装，更重要的是，它允许 UAs 根据情况改变断行。例如，UA 可以对短行文本使用更宽松的断行规则，对长行文本使用更严格的断行规则。实际上，“auto”允许用户代理根据需要在“loose”、“normal”和“strict”值之间进行切换，甚至可能在单个元素中逐行切换。

Doubtless you can infer that those other values have the following general meanings:

> 毫无疑问，你可以推断出这些其他的价值具有以下一般意义:

`loose`

This value imposes the “least restrictive” rules for wrapping text, and is meant for use when line lengths are short, such as in newspapers.

> 此值对换行文本施加“最少限制”规则，用于行长度较短的情况，如在报纸中。

`normal`

This value imposes the “most common” rules for wrapping text. What exactly “most common” means is not precisely defined, though there is the aforementioned list of recommended behaviors.

> 此值应用“最常见”的文本换行规则。“最常见”的确切含义并没有精确定义，尽管有前面提到的推荐行为列表。

`strict`

This value imposes the “most stringent” rules for wrapping text. Again, this is not precisely defined.

> 此值对文本换行施加“最严格”的规则。这也没有精确定义。

### 6.9.1 Wrapping Text

After all that information about hyphenation and soft wrapping, what happens when text overflows its container anyway? That’s what `overflow-wrap` addresses.

<Cards cards="overflow-wrap" />

This property couldn’t be more straightforward. If the default value of `normal` is in effect, then wrapping happens as normal; which is to say, between words or as directed by the language. If `break-word` is in effect, then wrapping can happen in the middle of words. Figure 6-43 illustrates the difference.

> 在所有关于连字符和软包装的信息之后，当文本溢出其容器时会发生什么?这就是“溢出-换行”的含义。

<Figures figure="6-43">Overflow wrapping</Figures>

<Tips tips="blue">Note that <code>overflow-wrap</code> can only operate if the value of <code>white-space</code> allows line wrapping. If it does not (e.g., with the value <code>pre</code>), then <code>overflow-wrap</code> has no effect.</Tips>

Where `overflow-wrap` gets complicated is in its history and implementation. Once upon a time there was a property called `word-wrap` that did exactly what `overflow-wrap` does. The two are so identical that the specification specifically states that user agents “must treat `word-wrap` as an alternate name for the `overflow-wrap` property, as if it were a shorthand of `overflow-wrap`.”

> “overflow-wrap”的复杂之处在于它的历史和实现。从前有一个叫做“word-wrap”的属性，它的功能与“overflow-wrap”完全相同。两者是如此相似，以至于规范明确规定用户代理“必须将‘word-wrap’作为‘overflow-wrap’属性的替代名称，就好像它是‘overflow-wrap’的缩写一样。”

Sadly, browsers didn’t always do this, and `word-wrap` was better supported. For this reason, it’s common to use both for backward compatibility:

> 遗憾的是，浏览器并不总是这样做，“自动换行”得到了更好的支持。出于这个原因，在向后兼容性中，这两种方法都很常见:

```css
pre {
  word-wrap: break-word;
  overflow-wrap: break-word;
}
```

As of late 2017, `overflow-wrap` enjoys very widespread supports, so it’s pretty safe to use.

> 到 2017 年底，“overflow-wrap”得到了广泛的支持，所以使用起来很安全。

While `overflow-wrap: break-word` may appear very similar to `word-break: break-all`, they are not the same thing. To see why, compare the second box in Figure 6-43 to the top middle box in Figure 6-42. As it shows, `overflow-wrap` only kicks in if content actually overflows; thus, when there is an opportunity to use whitespace in the source to wrap lines, `overflow-wrap` will take it. By contrast, `word-break: break-all` will cause wrapping when content reaches the wrapping edge, regardless of any whitespace that comes earlier in the line.

> 虽然“overflow-wrap: break-word”可能看起来与“word-break: break-all”非常相似，但它们不是一回事。要查看原因，请将图 6-43 中的第二个框与图 6-42 中的顶部中间框进行比较。正如它所显示的，“overflow-wrap”只有在内容确实溢出时才会出现;因此，当有机会在源代码中使用空白来换行时，“overflow-wrap”将接受它。相比之下，“word-break: break-all”将在内容到达换行边缘时进行换行，而不考虑行前面的任何空格。

## 6.10 Writing Modes

If you’re reading this book in English or any number of other mainly Western languages, then you’re reading the text left to right and top to bottom, which is the flow direction of English. Not every language runs this way. There are many right-to-left and top-to-bottom languages such as Hebrew and Arabic, and many languages that can be written primarily top-to-bottom. Some of the latter are secondarily left to right, such as Chinese and Japanese, whereas others are right to left, like Mongolian.

> 如果你正在读这本书的英文版本，或者其他一些主要是西方语言的版本，那么你正在从左到右，从上到下阅读文本，这就是英语的流动方向。不是所有的语言都是这样运行的。有许多从右到左和从上到下的语言，如希伯来语和阿拉伯语，还有许多语言主要是由上到下编写的。后者中有一些是从左到右的，如汉语和日语，而另一些是从右到左的，如蒙古语。

### 6.10.1 Setting Writing Modes

The property used for specifying one of the three available writing mode is, of all things, `writing-mode`.

> 用于指定三种可用写入模式之一的属性是“写入模式”。

<Cards cards="writing-mode" />

The default value, `horizontal-tb`, means “a horizontal inline direction, and a top-tobottom block direction.” This covers all Western and some Middle Eastern languages, which may differ in the direction of their horizontal writing. The other two values offer a vertical inline direction, and either a right-to-left or left-to-right block direction. All three are illustrated in Figure 6-44.

> 默认值“horizontalt -tb”表示“一个水平的内联方向，一个从上到下的块方向”。这包括所有的西方和一些中东语言，它们可能在水平方向上有所不同。其他两个值提供了一个垂直的内联方向，以及一个从右到左或从左到右的块方向。图 6-44 展示了这三种方法。

<Figures figure="6-44">Writing modes</Figures>

Notice how the lines are strung together in the two vertical examples. If you tilt your head to the right, the text in `vertical-rl` is at least readable. The text in `vertical-lr`, on the other hand, is difficult to read because it appears to flow from bottom to top, at least when arranging English text. This is not a problem in languages which actually use `vertical-lr` flow, such as form of Japanese. As of late 2017, vertical flows can only have the inline direction go from top to bottom.

> 请注意这两个垂直示例中的线条是如何串在一起的。如果你的头向右倾斜，“vertical-rl”中的文字至少是可读的。另一方面，“vertical-lr”中的文字很难阅读，因为它似乎是从下到上流动的，至少在安排英语文本时是这样。这在实际使用“垂直-lr”流的语言(如日语)中不是问题。截至 2017 年底，垂直流只能让内联方向从上到下。

It is possible to create bottom-to-top vertical flows of Western-language text by applying `vertical-rl` to an element and then rotating the element 180 degrees with CSS Transforms (see Chapter 16). This presents a bottom-to-top, left-to-right visual flow. Using `vertical-lr` and rotating it creates a bottom-to-top, right-to-left flow. Both are illustrated in Figure 6-45:

> 通过对一个元素应用“vertical-rl”，然后用 CSS 变换将元素旋转 180 度，可以创建西方语言文本的自下而上的垂直流(参见第 16 章)。这表示一个自下而上、从左到右的视觉流。使用“垂直-lr”和旋转它创建一个自下而上，从右到左的流动。两者在图 6-45 中都有说明:

```css
.flip {
  transform: rotate(180deg);
}
#one {
  writing-mode: vertical-rl;
}
#two {
  writing-mode: vertical-lr;
}
```

<Figures figure="6-45">Flipping vertical writing modes</Figures>

The challenge of working with text like that is that everything is flipped, which means what we see is at odds with what’s actually happening. The text of `vertical-rl` (vertical-right-to-left) is visually progressing left to right, for example.

> 处理这样的文本的挑战在于，所有的东西都被翻转了，这意味着我们看到的与实际发生的是不一致的。例如，“vertical-rl”(垂直-从右到左)的文本在视觉上是从左到右进行。

The same problem arises when applying inline block-alignment properties such as `vertical-align`. In vertical writing modes, the block direction is horizontal, which means vertical alignment of inline elements actually causes them to move horizontally. This is illustrated in Figure 6-46.

> 当应用诸如“垂直对齐”之类的内联块对齐属性时，也会出现相同的问题。在垂直书写模式中，块的方向是水平的，这意味着内联元素的垂直对齐实际上会导致它们水平移动。如图 6-46 所示。

<Figures figure="6-46">Writing modes and “vertical” alignment</Figures>

All the super- and subscript elements cause horizontal shifts, both of themselves and the placement of the lines they occupy, even through the property used to move them is `vertical-align`. As described earlier, the vertical displacement is with respect to the line box, where the box’s baseline is defined as horizontal—even when it’s being drawn vertically.

> 所有的上标元素和下标元素都会引起水平位移，它们本身和它们所占据的线条的位置都是如此，甚至通过用来移动它们的属性是“垂直对齐”。如前所述，垂直位移是相对于线框的，其中框的基线被定义为水平，即使是在垂直绘制时也是如此。

Confused? It’s OK. Writing modes are likely to confuse you, because it’s such a different way of thinking `and` because old assumptions in the CSS specification clash with the new capabilities. If there had been vertical writing modes from the outset, `vertical-align` would likely have a different name—`inline-align` or something like that. (Maybe one day that will happen.)

> 困惑吗?没关系。编写模式很可能会使您感到困惑，因为这是一种完全不同的思维方式，而且 CSS 规范中的旧假设与新功能相冲突。如果从一开始就有垂直的书写模式，“垂直对齐”可能会有一个不同的名字——“内对齐”或类似的东西。(也许有一天会实现。)

One last note: if you’re already used to CSS Transforms, you might be tempted to think of these vertical writing modes as equivalent to rotating the text 90 degrees. They are `not` the same, for two reasons. One, this only appears to be the case for `vertical-rl`; `vertical-lr` has the look of text that flows “bottom to top.” Two, the cardinal points don’t change when flowing text vertically. The top is still the top, in other words. This is illustrated by the following styles, whose results are depicted in Figure 6-47:

> 最后一点提示:如果您已经习惯了 CSS 转换，您可能会认为这些垂直书写模式等同于将文本旋转 90 度。它们“不一样”，有两个原因。第一，这似乎只是“垂直-rl”的情况;“垂直-lr”看起来像是“从下到上”的文字。第二，当文字垂直流动时，基本点不会改变。换句话说，顶部仍然是顶部。如下图所示，其结果如图 6-47 所示:

```css
.boxed {
  border-top: 3px solid red;
  border-left: 3px dashed tan;
}
#one {
  writing-mode: vertical-rl;
}
#two {
  writing-mode: vertical-lr;
}
```

<Figures figure="6-47">Writing modes and the “cardinal” directions of CSS</Figures>

In both cases, the top border is solid red, and the left border is dashed tan. The cardinal points don’t rotate with the text—because the text isn’t rotated. It’s being flowed in a different way.

> 在这两种情况下，上面的边框都是纯红色的，左边的边框是棕色的虚线。基点不随文本旋转，因为文本没有旋转。它以不同的方式流动。

Now here’s where it gets unusual. While the borders don’t migrate around the element box, margins `can`, but not due to anything in the CSS specification.

> 这就是它不寻常的地方。虽然边框不会在元素框中移动，但边距“可以”移动，但这与 CSS 规范无关。

This happens because user agents (at least as of late 2017) maintain internal styles that relate to the start and end of the element in the block direction. In languages that flow top to bottom, then the start and end of the element’s block direction are its top and bottom sides. But in vertical writing, the block direction is right to left or left to right. Thus, you can set up a bunch of paragraphs to flow vertically, and if you leave the margins alone, what would normally be top and bottom margins will become left and right margins. You can see this effect in Figure 6-48, which illustrated the result of the following styles:

> 这是因为用户代理(至少在 2017 年年底)维护与块方向中元素的开始和结束相关的内部样式。在从上到下流动的语言中，元素块方向的开始和结束是它的顶部和底部。但在垂直书写中，块的方向是从右到左或从左到右。因此，你可以设置一组垂直流动的段落，如果不考虑页边距，通常的顶部和底部页边距将变成左侧和右侧页边距。你可以在图 6-48 中看到这种效果，它展示了以下几种风格的效果:

```css
p {
  margin-top: 1em;
}
#one {
  writing-mode: vertical-rl;
}
#two {
  writing-mode: vertical-lr;
}
```

<Figures figure="6-48">The placement of UA default margins</Figures>

There are the top margins, as declared, right along the tops of the two paragraphs. The empty space to the side of each paragraph is created by the block-start and blockend margins. If we explicitly set the right and left margins to zero, then the space between the paragraphs would be removed.

> 正如所声明的那样，两段的顶部都有空白处。每个段落旁边的空白是由块开始和块结束边距创建的。如果我们显式地将左右边距设置为 0，那么段落之间的空格将被删除。

Remember: this happens because user agents, by default, represent the margins of text elements using properties like `block-start-margin` (which is not an actual property in CSS, at least not yet). If you explicitly set top, bottom, or side margins using properties like `margin-top`, then they will be applied to the element box just as borders were: top margin on top, right margin to the right, and so on.

> 请记住:这是因为用户代理在默认情况下使用“block-start-margin”这样的属性来表示文本元素的边距(这在 CSS 中不是一个实际的属性，至少现在还不是)。如果您使用类似“margin-top”的属性显式地设置顶部、底部或边距，那么它们将与边框一样应用于元素框:顶部的边框、右侧的边框等等。

### 6.10.2 Changing Text Orientation

Once you’ve settled on a writing mode, you may decide you want to change the orientation of characters within those lines of text. There are many reasons you might want to do this, not least of which are situations where different writing systems are commingled, such as Japanese text with English words or numbers mixed in. In these cases, `text-orientation` is the answer.

> 一旦确定了写作模式，就可以决定更改这些文本行的字符方向。这样做的原因有很多，尤其是不同的书写系统混合在一起的情况，比如日语文本中混合了英语单词或数字。在这些情况下，“文本导向”就是答案。

<Cards cards="text-orientation" />

The effect of `text-orientation` is to affect how characters are oriented. What that means is best illustrated by the following styles, rendered in Figure 6-49:

> “文本导向”的作用是影响字符的导向。这意味着最好的说明了以下风格，在图 6-49:

```css
.verts {
  writing-mode: vertical-lr;
}
#one {
  text-orientation: mixed;
}
#two {
  text-orientation: upright;
}
#thr {
  text-orientation: sideways;
}
```

<Figures figure="6-49">Text orientation</Figures>

Across the top of Figure 6-49 is a basically unstyled paragraph of mixed Japanese and English text. Below that, three copies of that paragraph, using the writing mode `vertical-lr`. In the first of the three, `text-orientation: mixed`, writes the horizontal-script characters (the English) sideways, and the vertical-script characters (the Japanese) `upright`. In the second, all characters are upright, including the English characters. In the third, all characters are `sideways`, including the Japanese characters.

> 图 6-49 的上方是一段混合了日语和英语的文字，基本上没有什么风格。在该段下面，用“垂直-lr”的书写模式复制该段三份。在这三种字体中的第一种，“文本导向:混合”，横向书写(英文)，纵向书写(日文)“正直”。第二种是所有的汉字都是直立的，包括英语汉字。第三种，所有的角色都是“横向的”，包括日本角色。

### 6.10.3 Declaring Direction

Harking back to the days of CSS2, there are a pair of properties that can be used to affect the direction of text by changing the inline baseline direction: `direction` and `unicode-bidi`.

> 回到 CSS2 的时代，有一对属性可以通过改变内联基线方向来影响文本的方向:‘direction’和‘unicode-bidi’。

<Tips tips="orange">The CSS specification explicitly warns <code>against</code> using <code>direction</code> and <code>unicode-bidi</code> in CSS when applied to HTML documents. To quote: “Because HTML <code>[user agents]</code> can turn off CSS styling, we recommend…the HTML <code>dir</code> attribute and <code>< bdo></code> element to ensure correct bidirectional layout in the absence of a style sheet.” The properties are covered here because they may appear in legacy stylesheets.</Tips>

<Cards cards="direction" />

The `direction` property affects the writing direction of text in a block-level element, the direction of table column layout, the direction in which content horizontally overflows its element box, and the position of the last line of a fully justified element. For inline elements, direction applies only if the property `unicode-bidi` is set to either `embed` or `bidi-override` (See the following description of `unicode-bidi`).

> “方向”属性影响块级元素中文本的写入方向、表列布局的方向、内容水平地溢出其元素框的方向以及完全对齐元素的最后一行的位置。对于内联元素，只有当属性“unicode-bidi”设置为“embed”或“bi -override”时，方向才适用(请参阅下面对“unicode-bidi”的描述)。

Although `ltr` is the default, it is expected that if a browser is displaying right-to-left text, the value will be changed to `rtl`. Thus, a browser might carry an internal rule stating something like the following:

> 虽然“ltr”是默认值，但是如果浏览器显示从右向左的文本，那么这个值将被更改为“rtl”。因此，一个浏览器可能会有一个内部规则，类似如下:

```css
*:lang(ar),
*:lang(he) {
  direction: rtl;
}
```

The real rule would be longer and encompass all right-to-left languages, not just Arabic and Hebrew, but it illustrates the point.

> 真正的规则会更长，包括所有从右到左的语言，不只是阿拉伯语和希伯来语，但它说明了这一点。

While CSS attempts to address writing direction, Unicode has a much more robust method for handling directionality. With the property `unicode-bidi`, CSS authors can take advantage of some of Unicode’s capabilities.

> 虽然 CSS 试图解决写入方向的问题，但是 Unicode 有一个更健壮的方法来处理方向性。通过“Unicode -bidi”属性，CSS 作者可以利用 Unicode 的一些功能。

<Cards cards="unicode-bidi" />

Here we’ll simply quote the value descriptions from the CSS 2.1 specification, which do a good job of capturing the essence of each value:

> 在这里，我们将简单地引用 CSS 2.1 规范中的值描述，它很好地捕捉了每个值的本质:

`normal`

The element does not open an additional level of embedding with respect to the bidirectional algorithm. For inline-level elements, implicit reordering works across element boundaries.

> 对于双向算法，元素不会打开额外的嵌入级别。对于内层元素，隐式重新排序可以跨元素边界进行。

`embed`

If the element is inline-level, this value opens an additional level of embedding with respect to the bidirectional algorithm. The direction of this embedding level is given by the `direction` property. Inside the element, reordering is done implicitly. This corresponds to adding an LRE (U+202A; for `direction: ltr`) or an RLE (U+202B; for `direction: rtl`) at the start of the element and a PDF (U+202C) at the end of the element.

> 如果元素是内联级的，则此值相对于双向算法打开一个附加的嵌入级别。这个嵌入层的方向由“方向”属性给出。在元素内部，重新排序是隐式完成的。这相当于添加一个 LRE (U+202A;表示“方向:ltr”)或 RLE (U+202B;在元素的开始和一个 PDF (U+202C)在元素的结束。

`bidi-override`

This creates an override for inline-level elements. For block-level elements, this creates an override for inline-level descendants not within another block. This means that, inside the element, reordering is strictly in sequence according to the `direction` property; the implicit part of the bidirectional algorithm is ignored. This corresponds to adding an LRO (U+202D; for `direction: ltr`) or RLO (U+202E; for `direction: rtl`) at the start of the element and a PDF (U+202C) at the end of the element.

> 这将为内联级元素创建一个覆盖。对于块级元素，这将为不在另一个块内的内联级后代创建覆盖。这意味着，在元素内部，重新排序是严格按照“direction”属性的顺序进行的;忽略了双向算法的隐式部分。这相当于添加一个 LRO (U+202D;for ' direction: ltr ')或 RLO (U+202E;在元素的开始和一个 PDF (U+202C)在元素的结束。

## 6.11 Summary

Even without altering the font face, there are many ways to change the appearance of text. There are classic effects such as underlining, but CSS also enables you to draw lines over text or through it, change the amount of space between words and letters, indent the first line of a paragraph (or other block-level element), align text in various ways, exert influence over the hyphenation and line breaking of text, and much more. You can even alter the amount of space between lines of text. There is also support in CSS for languages other than those that are written left-to-right, top-to-bottom. Given that so much of the web is text, the strength of these properties makes a great deal of sense. Recent developments in improving text legibility and placement are likely only the beginnings of what we will eventually be able to do with text styling.

> 即使不改变字体面，也有许多方法可以改变文本的外观。有经典的反应如强调,但 CSS 还使您能够在文本或通过绘制线条,改变单词和字母之间的空间,一个段落的第一行缩进(或其他块级元素),文本对齐以各种方式,在施加影响断字和线断裂的文本,等等。您甚至可以更改文本行与行之间的间距。除了从左到右、从上到下编写的语言之外，CSS 中还支持其他语言。考虑到 web 的大部分内容都是文本，这些属性的强度就很有意义了。最近在提高文本可读性和位置方面的发展可能只是我们最终能够使用文本样式所做事情的开始。
