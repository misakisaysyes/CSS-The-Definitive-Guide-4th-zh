# 第 8 章 Padding, Borders, Outlines 和 Margins

In the previous chapter, we talked about the basics of element display. In this chapter, we’ll look at the CSS properties and values you can use to change the specific appearance of elements that are displayed. These include the padding, borders, and margins around an element, as well as any outlines that may be added.

> 在前一章中，我们讨论了元素显示的基础知识。在本章中，我们将研究 CSS 属性和值，您可以使用它们来更改所显示元素的特定外观。这些包括元素周围的填充、边框和边距，以及可能添加的任何轮廓。

## 8.1 Basic Element Boxes

As you may be aware, all document elements generate a rectangular box called the element box, which describes the amount of space that an element occupies in the layout of the document. Therefore, each box influences the position and size of other element boxes. For example, if the first element box in the document is an inch tall, then the next box will begin at least an inch below the top of the document. If the first element box is changed and made to be two inches tall, every following element box will shift downward an inch, and the second element box will begin at least two inches below the top of the document.

> 您可能已经注意到，所有文档元素都会生成一个名为 element box 的矩形框，它描述了一个元素在文档布局中所占的空间量。因此，每个盒子都会影响其他元素盒子的位置和大小。例如，如果文档中的第一个元素框是一英寸高，那么下一个框将在文档顶部以下至少一英寸处开始。如果将第一个元素框更改为 2 英寸高，那么下面的每个元素框将向下移动 1 英寸，而第二个元素框将从文档顶部以下至少 2 英寸处开始。

By default, a visually rendered document is composed of a number of rectangular boxes that are distributed so that they don’t overlap. Also, within certain constraints, these boxes take up as little space as possible while still maintaining a sufficient separation to make clear which content belongs to which element.

> 默认情况下，可视化呈现的文档是由一些矩形框组成的，这些矩形框分布在不同的地方，这样它们就不会重叠。此外，在某些约束条件下，这些框占用尽可能少的空间，同时仍然保持分离，以便明确哪些内容属于哪些元素。

Boxes can overlap if they have been manually positioned, and visual overlap can occur if negative margins are used on normal-flow elements.

> 如果手动定位方框，它们可能会重叠;如果在正常流元素上使用负边距，则可能出现视觉重叠。

In order to understand how margins, padding, and borders are handled, you must understand the box model, illustrated in Figure 8-1.

> 为了理解如何处理边距、填充和边框，您必须理解 box 模型，如图 8-1 所示。

### Width and Height

It’s fairly common to explicitly define the width of an element, and historically much less common to explicitly define the height. By default, the width of an element is defined to be the distance from the left inner edge to the right inner edge, and the height is the distance from the inner top to the inner bottom. The properties that affect these distances are, unsurprisingly, called `height` and `width`.

> 显式定义元素的宽度相当常见，而在历史上显式定义元素的高度则少见得多。默认情况下，元素的宽度定义为从左内边缘到右内边缘的距离，而高度定义为从内顶部到内底部的距离。毫不奇怪，影响这些距离的属性被称为“高度”和“宽度”。

One important note about these two properties: they don’t apply to inline nonreplaced elements. For example, if you try to declare a height and width for a hyperlink that’s in the normal flow and generates an inline box, CSS-conformant browsers must ignore those declarations. Assume that the following rule applies:

> 关于这两个属性有一点需要注意:它们不应用于内联的不可替换元素。例如，如果您试图为正常流中的超链接声明高度和宽度并生成内联框，符合 css 的浏览器必须忽略这些声明。假设以下规则适用:

```css
a:link {
  color: red;
  background: silver;
  height: 15px;
  width: 60px;
}
```

You’ll end up with red unvisited links on silver backgrounds whose height and width are determined by the content of the links. They will `not` have content areas that are 15 pixels tall by 60 pixels wide. If, on the other hand, you add a `display` value, such as `inline-block` or `block`, then `height` and `width` will set the height and width of the links’ content areas.

> 你会在银色背景上得到一个红色的未访问链接，它的高度和宽度是由链接的内容决定的。他们将“不”有 15 像素高 60 像素宽的内容区域。另一方面，如果您添加了一个“显示”值，例如“内联块”或“块”，那么“高度”和“宽度”将设置链接内容区域的高度和宽度。

In the course of this chapter, we’ll usually keep the discussion simple by assuming that the height of an element is always calculated automatically. If an element is eight lines long, and each line is an eighth of an inch tall, then the height of the element is one inch. If it’s 10 lines tall, then the height is 1.25 inches. In either case, the height is determined by the content of the element, not by the author. It’s rarely the case that elements in the normal flow have a set height.

> 在本章的过程中，我们通常通过假设元素的高度总是自动计算来简化讨论。如果一个元素有 8 行，每一行都是 1/8 英寸高，那么元素的高度就是 1 英寸。如果是 10 行，那么高度是 1.25 英寸。在这两种情况下，高度是由元素的内容决定的，而不是由作者决定的。正常流中的元素很少有固定的高度。

## 8.2 Padding

Just beyond the content area of an element, we find its padding, nestled between the content and any borders. The simplest way to set padding is by using the property padding.

As you can see, this property accepts any length value, or a percentage value. So if you want all h2 elements to have 1 em of padding on all sides, it’s this easy (see Figure 8-2):

```css
h2 {
  padding: 2em;
  background-color: silver;
}
```

//

As Figure 8-2 illustrates, the background of an element extends into the padding by default. If the background is transparent, this will create some extra transparent space around the element’s content, but any visible background will extend into the padding area (and beyond, as we’ll see in a later section).

> 如图 8-2 所示，默认情况下，元素的背景扩展到填充中。如果背景是透明的，这将在元素的内容周围创建一些额外的透明空间，但是任何可见的背景都将扩展到填充区域(以及其他区域，我们将在后面的小节中看到)。

By default, elements have no padding. The separation between paragraphs, for example, has traditionally been enforced with margins alone (as we’ll see later on). It’s also the case that, without padding, the border of an element will come very close to the content of the element itself. Thus, when putting a border on an element, it’s usually a good idea to add some padding as well, as Figure 8-3 illustrates.

> 默认情况下，元素没有填充。例如，传统上，段落之间的分隔仅靠边距执行（我们将在后面介绍）。在没有填充的情况下，元素的边框也会非常接近元素本身的内容。因此，在元素上加上边框时，通常最好还添加一些填充，如图8-3所示。

### 8.2.1 Replicating Values

### 8.2.2 Padding Single-Side Padding

### 8.2.3 Percentage Values and Padding

### 8.2.4 Padding and Inline Elements

### 8.2.5 Padding and Replaced Elements

## 8.3 Borders

### 8.3.1 Borders with Style

### 8.3.2 Border Widths

### 8.3.3 Border Colors

### 8.3.4 Shorthand Border Properties

### 8.3.5 Global Borders

### 8.3.6 Borders and Inline Elements

### 8.3.7 Rounding Border Corners

### 8.3.8 Image Borders

## 8.4 Outlines

### 8.4.1 Outline Styles

### 8.4.2 Outline Width

### 8.4.3 Outline Color

### 8.4.4 How They Are Different

## 8.5 Margins

### 8.5.1 Length Values and Margins

### 8.5.2 Percentages and Margins

### 8.5.3 Single-Side Margin Properties

### 8.5.4 Margin Collapsing

### 8.5.5 Negative Margins

### 8.5.6 Margins and Inline Elements

## 8.6 Summary
