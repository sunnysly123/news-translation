> * 原文地址：[The Ultimate Guide to Flexbox — Learning Through Examples](https://www.freecodecamp.org/news/the-ultimate-guide-to-flexbox-learning-through-examples-8c90248d4676/)
> * 原文作者：[Emmanuel Ohans](https://www.freecodecamp.org/news/author/emmanuel/)
> * 译者：sunnysly123
> * 校对者：

![The Ultimate Guide to Flexbox — Learning Through Examples](https://cdn-media-1.freecodecamp.org/images/1*9vcCT6S_dFJqR6yed6Vmqw.png)

![](https://cdn-media-1.freecodecamp.org/images/DDLwRS3Jad5brv0RIH2r5K2YxqcvAa1vBThw)

注意 — 这篇文章篇幅较长，你可以在[这里][1]下载文章后离线阅读。

理解 **Flexbox**最好的方式是什么？学好基础，再不断练习。这就是这篇文章要做的事情。

### 要注意的几点

-   这篇文章预设你是一名中级开发者，且对Flexbox有点了解。但是。。。
-   如果你对css有些了解，但是没有接触过Flexbox，[我写了一篇通用指导（免费文章，阅读时间约为46分钟）][2].
-   如果你对CSS掌握的不是很好，我推荐你阅读 [CSS全面（实用）指南 (74课时的付费课程)][3]。
-   你不需要遵照这里列出的示例顺序。
-   Flexbox只是一种布局的技巧。实际项目应用需要更多的布局样式。
-   当你看到例如 `div.ohans` 的例子，这代表类名是  `ohans`的 div

### 例1: 如何用 Flexbox 完成一个影片集

使用 Flexbox 实现横向纵向排列比很多人想象的要简单。

例如一个如下的简单标记文本：

```
<main class="gallery">  <img src="/sample.jpg">  <img src="/sample.jpg">  <img src="/sample.jpg">  <img src="/sample.jpg">  <img src="/sample.jpg">  <img src="/sample.jpg">  <img src="/sample.jpg">  <img src="/sample.jpg">  <img src="/sample.jpg">  <img src="/sample.jpg"></main>
```

`main.gallery` 里有十张图片。

我们要用  `main.gallery`  排列在可见屏幕上。

```
.gallery {   min-height: 100vh}
```

#### 有关图片的简单提示

图片默认是有宽高的  `inline-block`  元素。除非有限定大小，例如图片太大不能排列在一行，否则他们都会排列在一行。

#### 起始点

所有图片放在一起的显示效果如下：

![](https://cdn-media-1.freecodecamp.org/images/s2ntfDqrLewl66sGtavdhgQybTyD2JX520r2)

10张宽高不变地排列在一起，合适的时候换行，顺序排放 ;)

现在，看下Flexbox的效果:

```
.gallery {    display: flex }
```

在这点上，图片的默认属性已经发生改变。他们从  `inline-block`  布局变成了  `flex-items.`

由于  `.gallery`  里的Flexbox布局，里面的图片会被压缩排列在一行内，而且他们会被纵向拉伸称这样：

![](https://cdn-media-1.freecodecamp.org/images/sEzCWC3d-xoorKjDGf8TMdq6-ZxtOFMQjIST)

图片都被纵向拉伸挤在一行内，不能更丑 :(

这就是Flexbox布局的默认展示方式:

1.  将所有的子元素压在一行内，不换行。

这并不适用于图片库，因此我们可以这样改变：

```
.gallery {    flex-wrap: wrap}
```

这样所有的元素会在合适的时候换行，多行排列。

![](https://cdn-media-1.freecodecamp.org/images/JGAnqvkIeN-q8vh1beADx0XUrUE6SEZkGQFp)

因为wrap值的改变，图片都换行排列

2\. 现在图片有换行，但是仍然纵向拉伸。我们当然不想要这样扭曲的布局。

  `stretch`  显示是因为  `flex`  里默认的  `align-items`  值。

```
align-items: stretch
```

我们可以改成这样：

```
.gallery {  ...  align-items: flex-start}
```

这样图片不会拉伸，而是保持他们默认的宽和高。

如下所示，他们会在纵向保持首部对齐。

![](https://cdn-media-1.freecodecamp.org/images/02VgeT3SyoxuWFwkqyD1pzEjFzUjMH160mn0)

现在图片都是没有扭曲展示，这也很像我们在使用Flexbox之前的效果。

Now we have our Flexbox powered gallery.现在我们就要开始用Flexbox来强大图片集。

#### 使用Flexbox的优点

此刻Flexbox似乎没展现出什么优势，图片还是像使用  **Flexbox**  之前一样。

除了能得到一个免费的响应式图片集外，使用Flexbox的另一个优势就是他带来的对齐选项。

还记得flex容器  `.gallery`  设定的样式`flex-direction: row`  `justify-content: flex-start`  和  `align-items: flex-start.`

如下所示，改变默认值，我们就可以立马改变图片库的布局。

```
.gallery {   ...   justify-content:center;}
```

![](https://cdn-media-1.freecodecamp.org/images/etSBjIv9EwausQZC8PCe3tdHj0JovaLXkNvs)

图片在水平上完美居中。

如上所示，这会让图片水平居中。

```
.gallery {   ...   justify-content:center;   align-items: center;}
```

![](https://cdn-media-1.freecodecamp.org/images/jSx35Bma2fYhAISiEg0B3TcZanxoy0hPOb8D)

再进一步，我们可以让图片完美水平对齐（无论是水平还是垂直）

如上所示，这可以让图片在  `.gallery` 内水平和垂直都居中。

你可以通过Flexbox的布局方式随意选择你想要的对齐选项。

你可以通过  [CodePen][4]查看Flexbox图片库的实时布局效果。

### 例2：如何通过Flexbox布局卡片 

卡片在网上很流行，无论是Google, Twitter 还是 Pinterest，每个网站都在使用卡片。

卡片是一种在大小可变容器内组合相关信息的页面设计方式，视觉上很像一种玩的卡片。

使用卡片有很多好的地方，其中一个常用的就是臭名昭著的价格表。

![](https://cdn-media-1.freecodecamp.org/images/wjb-g2V7hV6IvRbGaDHYmAePhTjwR5ZeekkX)

价格表模型

让我们来建一个。

#### 标记

我们给每个卡片设定一个如下的标记：

```
<section class="card">  <header>  </header>
```

```
  <ul>    <li></li>    <li></li>    <li></li>  </ul>  <button></button></section>
```

这里有至少3个卡片，我们把这些卡片包在  `div.cards`里

```
<div class="cards"></div>
```

现在已经有了一个父元素。在这个例子中，父元素充满整个视图。

```
.cards {   min-height: 100vh}
```

#### 建立Flexbox布局

下面的代码块新建了一个在  `.cards` 里面的Flexbox布局样式。

```
.cards {  display: flex;  flex-wrap: wrap}
```

如果你还记得上一个例子，  `flex-wrap`  可以让  `flex-items`  换行。

由于子元素排列需要更大的宽度，所以子元素不能在父元素内排列时就会换行。

接下来我们给  `.card`  元素一个初始宽度。

使用Flexbox如下布局:

```
.card {  flex: 0 0 250px}
```

这个样式将  `flex-grow`  和  `flex-shrink`  的值设为0，  `flex-basis`  值为  `250px`。

这时，卡片会在页面的起始处对齐，并且垂直延伸。

![](https://cdn-media-1.freecodecamp.org/images/dkco2Y-Dru2WyMonIq51riqbYtjVr2Zn3E4T)

卡片首部对齐

这有时可能满足你的使用需求，但大部分情况下，都不行。

#### Flex容器的默认设置

上面的布局是由于flex容器的默认布局设置。

卡片在页面内靠顶部左边对齐，因为  `justify-content`  的值默认为  `flex-start`  。

同时，卡片垂直拉伸充满整个父元素的高度，因为  `align-items`  的默认值是  `stretch`  。

#### 改变默认值

我们可以通过改变Flexbox提供的默认值来达到更好的效果。

看下面几个例子：

![](https://cdn-media-1.freecodecamp.org/images/hq7D1wJINa5-DC77TMt4e517xOAG6C46yKZ3)

align-items: flex-start; justify-content: center

![](https://cdn-media-1.freecodecamp.org/images/R8-ShSWPknA8m7CBl1UNMj4qdbhycAIp1D9r)

align-items: flex-end; justify-content: center

![](https://cdn-media-1.freecodecamp.org/images/B9jkLQHZp7Cze2rEPkE8mzUfBDRWuf5nXFYP)

align-items: center; justify-content: center

你可以在[CodePen][5]看最终的效果。

### 例3：如何通过Flexbox创建网格布局

在这个例子中，我们要探讨整体的CSS 框架概念，这是很重要的一点。

#### 什么是网格布局？

网格是用来构建内容的一系列水平垂直相交引导线。

![](https://cdn-media-1.freecodecamp.org/images/06AK1XPmRT2w0zMezFzS2W50a8-xxwmujZEb)

一系列水平垂直相交引导线

如果你对Bootstrap这样的CSS框架比较熟悉，那可以确定之前你有使用过网格布局。

你的目标可能不同，但在这个例子中我们会考虑不同的网格布局类型。

我们先来看第一种，**basic grids**

#### 基本网格布局

![](https://cdn-media-1.freecodecamp.org/images/emC8Q5HRNl1dVcCGxvvheVNZYpQ0Ce05-MMc)

每套基础的网格都有同样大小的列

这些网格有以下特点：

-   网格单元格要平均布局并充满整行。
-   单元格高度一致。

使用Flexbox很容易实现这个效果，看下面这个标记文本：

```
<div class="row">  <div class="row_cell">1</div></div>
```

每个  `.row`  都是自己的flex容器。

  `.row`  里的每个元素也就是flex元素，所有的flex元素平均分布在一行中。

根据设计，可能有3个子元素

```
<div class="row">  <div class="row_cell">1/3</div>  <div class="row_cell">1/3</div>  <div class="row_cell">1/3</div></div>
```

或是6个子元素。

```
<div class="row">  <div class="row_cell">1/6</div>  <div class="row_cell">1/6</div>  <div class="row_cell">1/6</div>  <div class="row_cell">1/6</div>  <div class="row_cell">1/6</div>  <div class="row_cell">1/6</div></div>
```

也有可能是12个

```
<div class="row">  <div class="row_cell">1/12</div>  <div class="row_cell">1/12</div>  <div class="row_cell">1/12</div>  <div class="row_cell">1/12</div>  <div class="row_cell">1/12</div>  <div class="row_cell">1/12</div>  <div class="row_cell">1/12</div>  <div class="row_cell">1/12</div>  <div class="row_cell">1/12</div>  <div class="row_cell">1/12</div>  <div class="row_cell">1/12</div>  <div class="row_cell">1/12</div></div>
```

#### 解决方案

达到这个效果只需要两步：

1.  设置一个初始的Flexbox布局：

```
.row {   display: flex;}
```

2\. 扩大每个  `flex-item`  元素，让他们以相同比例均匀的布满整行：

```
.row_cell {   flex: 1}
```

就是这样

#### 方案解释。

```
flex: 1
```

`flex`  是  `flex-grow`  、  `flex-shrink`  和  `flex-basis`  三个不同Flexbox属性的缩写。

`flex: 1`  只有  `1`  的值，这个值代表的是`flex-grow` 属性。

而  `flex-shrink`  和  `flex-basis`  则分别设置为 `1`  和  `0`。

```
flex: 1  === flex: 1 1 0
```

#### 有具体数值的网格元素

有时候你需要的效果并不是同样大小的水平网格布局。

你可能想要一个元素是其他的两倍，或者一半。

![](https://cdn-media-1.freecodecamp.org/images/CKD3-ZUoxNAOJ-bp-cUZ0XcxnnMB1OvvA2yX)

水平网格布局中的元素是其他的两倍或3倍。

实现方式很简单。

对于这些明确的网格元素，只需要加一个这样的修饰符类：

```
.row_cell--2 {   flex: 2}
```

加上这个类，可以看到第一个  `div`  子元素代码如下：

```
<div class="row">  <div class="row_cell row_cell--2">2x</div>  <div class="row_cell">1/3</div>  <div class="row_cell">1/3</div></div>
```

加上  `.row__cell--2`  类名的元素会是其他默认元素的两倍大小。

占可用空间3倍的元素：

`.row_cell--3 {`  
`flex: 3`  
`}`

#### 有确定对齐方式的网格元素

多亏了Flexbox布局，我们不需要给每个元素设置特定的对齐值。你可以给任何一个元素设定不同的对齐方式。

通过下面的修饰符类，可以达到这样的效果：

```
.row_cell--top {  align-self: flex-start}
```

这可以让特定的元素在  `row` 内靠顶部对齐。

![](https://cdn-media-1.freecodecamp.org/images/rSpBVp7JoobnRoc0-Vsb6CjfzyKxO9c5pUwq)

应用.row\_cell — top 类可以让特定的元素在  `row`  内靠顶部对齐。

你也需要在标记文本中给特定元素加上这个类。看文本中第一个  `div`  子元素的写法：

```
<div class="row">  <div class="row_cell row_cell--top"></div>  <div class="row_cell"></div>  <div class="row_cell"></div></div>
```

下面是其他可选的对齐方式：

```
.row_cell--bottom {  align-self: flex-end}
```

![](https://cdn-media-1.freecodecamp.org/images/V76ETVyzFX4E7HLQ3MLr03LSH6GkYnvjEzNa)

给特定的元素加上.row\_cell — bottom类会让它在  `row`  内靠底部对齐。

```
.row_cell--center {  align-self: center}
```

![](https://cdn-media-1.freecodecamp.org/images/N-KfRijROiUyGtSj6RTAZmZjNZZ5A3Djf2NA)

给特定的元素加上.row\_cell — center类会让它在  `row`  内居中对齐。

#### 整行对齐

  **entire**  整行的的子元素也可以像特定的元素一样对齐。

使用下面的修饰符类达到这样的效果：

```
.row--top {   align-items: flex-start}
```

![](https://cdn-media-1.freecodecamp.org/images/le3bablkysAG-j-JEQQdHyBvvjiCbIfZP2Bs)

一行上的三个元素都靠顶部对齐。

需要注意的一个重点是，  `.row--top`  一定要被加在  `row`  或是父元素  `flex-container`  上。

```
<div class="row row--top">  <div class="row_cell"></div>  <div class="row_cell"></div>  <div class="row_cell"></div></div>
```

其他的对齐选项见下：

```
.row--center {   align-items: center}
```

![](https://cdn-media-1.freecodecamp.org/images/NVv3xZxxaIbyPHDJTxp5LdcG-Be0wolyXiCb)

整行的三个元素都居中对齐。

```
.row--bottom {   align-items: flex-end}
```

![](https://cdn-media-1.freecodecamp.org/images/OsI1AJj-F4BMIJQAMN82bY6MXqTxvwmZkw3J)

整行的三个元素都靠底部对齐

#### 巢状网格

没有特殊的设置，这些  `rows`  可以在内部巢状布局。

![](https://cdn-media-1.freecodecamp.org/images/2eyhYZJlDdZXJkiLuwGYSoB83KKPxnfgfjCg)

一行内有两个元素，一个是另一个的两倍大小。在较大的元素里，一行三个元素居中巢状排列。

你可以在  [created here][6]查看最终的布局效果。

#### 更多网格布局

当你可以用Flexbox垂直网格甚至更复杂的参数实现好看的网格构造时，就可以把这个最好的工具用于工作。学习，掌握然后使用  [CSS Grid Layout][7]，这是CSS网格布局中最基本的解决方案。

### 例4：如何使用Flexbox构建网站布局

社区通常不喜欢整个网站布局都使用Flexbox。

虽然我赞同这个看法，但是我也认为特定的情况下你可以不用考虑这么多。

我能给到最重要的一点建议是：

> **_在你需要的时候使用Flexbox布局_**

这点我会在下面的例子中解释。

#### 圣杯布局

比臭名昭著的 “**holy grail**”更好的网站布局方式是什么呢？

![](https://cdn-media-1.freecodecamp.org/images/9HvLwuqluns72rMdkVL4SMf5pyPQMxFb9mSi)

圣杯布局 — 头部, 页脚和3个其他的容器。

用Flexbox有两种方式可以实现这种布局。

The first is to have the layout built with Flexbox. Place the  `header`,  `footer`,  `nav`,  `article`  and  `aside`  all in one  `flex-container`.

Let’s begin with that.

#### The Markup

Consider the basic markup below:

```
<body>  <header>Header</header>  <main>    <article>Article</article>    <nav>Nav</nav>    <aside>Aside</aside>  </main>  <footer>Footer</footer></body>
```

Among others, there is a particular rule the holy grail adheres to. This rule has inspired the markup above:

The center column,  `article`  should appear first in the markup, before the two sidebars,  `nav`  and  `aside`.

![](https://cdn-media-1.freecodecamp.org/images/YDZbT2gN-JVcBRbvAkXYasm3Hqo-Q7VtxbU9)

“<article></article>” appears first in the markup, but is centered in the layout.

#### Initiate the Flexbox Formatting Context

```
body {   display: flex}
```

Because the child elements should stack from top to bottom, the default direction of the Flexbox must be changed.

```
body { ... flex-direction: column}
```

**1**. `header`  and  `footer`  should have a fixed width.

```
header,footer {  width: 20vh /*you can use pixels e.g. 200px*/}
```

**2.**`main`  must be made to fill the available remaining space within the  `flex-container`

```
main {   flex: 1}
```

Assuming you didn’t forget,  `flex: 1`  is equivalent to  `flex-grow: 1`  ,  `flex-shrink: 1`and  `flex-basis: 0`

![](https://cdn-media-1.freecodecamp.org/images/eBj3j7v59T5PYdH8sBCadGevCVyOlPfuMIqR)

This will cause  `main`  to “grow” and contain the available remaining space.

At this point, we need to take care of the contents within  `main`  which are  `article`,  `nav`and  `aside`.

Set up  `main`  as a  `flex-container`  :

```
main {  display: flex}
```

Have the  `nav`  and  `aside`  take up fixed widths:

```
nav,aside {  width: 20vw}
```

Ensure that  `article`  takes up the remaining available space:

```
article {   flex: 1}
```

![](https://cdn-media-1.freecodecamp.org/images/3--f-KqkBdvx8jv6n9mhmA354cP7OvgS4Ayz)

`"article"`  now takes up the remaining available space

There’s just one more thing to do now.

Re-order the  `flex-items`  so  `nav`  is displayed first:

```
nav {  order: -1}
```

![](https://cdn-media-1.freecodecamp.org/images/rN1l8s8aO44ecL8RBUIG824WpUNHBIyl5iLo)

The final result.  [https://codepen.io/ohansemmanuel/full/brzJZz/][8]

The  `order`  property is used to re-order the position of  `flex-items`.

All  `flex-items`  within a container will be displayed in  **increasing** `order`  values. The  `flex-item`  with the lowest  `order`  values appear first.

All  `flex-items`  have a default  `order`  value of  `0`.

#### The Holy Grail Layout (another solution)

The previous solution used a  `flex-container`  as the overall container. The layout is heavily dependent on Flexbox.

Let’s see a more “sane” approach. Take a look at the supposed final result again:

![](https://cdn-media-1.freecodecamp.org/images/UIy61i1OzIjdddu2W5i9NvL74JXjY5sclt8i)

The holy grail layout

`header`  and  `footer`  could be treated as block elements. Without any intervention, they will fill up the width of their containing element, and stack from top to bottom.

```
<body>  <header>Header</header>  <main>    <article>Article</article>    <nav>Nav</nav>    <aside>Aside</aside>  </main>  <footer>Footer</footer></body>
```

With this approach, the only  `flex-container`  needed would be  `main`.

The singular challenge with this approach is that you have to compute the height of  `main`  yourself.  `main`  should fill the available space besides the space taken up by the  `header`and  `footer.`

```
main {  height: calc(100vh - 40vh);}
```

Consider the code block above. It uses the CSS  `calc`  function to compute the height of  `main.`

Whatever your mileage, the height of  `main`  must be equal to  `calc(100vh — height of header — height of footer ).`

As in the previous solution, you must have given  `header`  and  `footer`  a fixed height. Then go ahead and treat  `main`  the same way as in the previous solution.

You may view the  [actual results here][9].

#### 2 column website layouts

Two column layouts are pretty common. They are also easily achieved using Flexbox.

![](https://cdn-media-1.freecodecamp.org/images/Mk-G8NgfEsSoMlzbafucKr5IUHOiSAcr4cEp)

2 column layout with a sidebar and main content area.

Consider the markup below:

```
<body>  <aside>sidebar</aside>  <main>main</main></body>
```

Initiate the Flexbox formatting context:

```
body {  display: flex;}
```

Give  `aside`  a fixed width:

```
aside {   width: 20vw}
```

Finally, ensure that  `main`  fills up the remaining available space:

```
main {  flex: 1}
```

That’s pretty much all there is to it.

### Example 5: Media Objects with Flexbox

Media Objects are everywhere. From tweets to Facebook posts, they seem to be the go to choice for most UI designs.

![](https://cdn-media-1.freecodecamp.org/images/hoOVQQcGFJ-EivoJRCqOTXynRzq88ye3zzE6)

Sample Tweet and Facebook post

Consider the markup below:

```
<div class="media">  <img class="media-object" src="/pic.jpg">  <div class="media-body">    <h3 class="media-heading"> Header </h3>    <p></p>  </div></div>
```

As you have guessed,  `.media`  will establish the Flexbox formatting context:

```
.media {   display: flex}
```

By default, the  `flex-items`  of a  `container`  are stretched along the vertical to fill the available height within the  `flex-container`.

Make sure the  `.media-body`  takes up all the remaining available space:

```
.media-body {   flex: 1}
```

![](https://cdn-media-1.freecodecamp.org/images/zJRJJ8NeVDHI1FNdnsKF5mpeRXjabOb-zVk9)

The box on the left stretches to fit the available screen. The media body takes up the remaining horizontal space within the media object (white)

Let’s fix the stretched box.

```
.media {  ...  align-items: flex-start}
```

![](https://cdn-media-1.freecodecamp.org/images/hkcBJNNimRRArL6iPiDoFN3UdSJSHdRazWlw)

The flex items are now aligned to the start of the media object. The image now takes it default’s size. No weird stretching :)

And that’s it.

#### A flipped Media Object

![](https://cdn-media-1.freecodecamp.org/images/GL7OTu019Ov2HtElcXKhObmhreC86yEDpKK0)

A flipped media object has the image on the other side (right) of the media object

You do not have the change the  `html`  source order to create a flipped media object.

Just re-order the  `flex-item`s like so:

```
.media-object {   order: 1}
```

This will have the image displayed after the  `.media-body`  and  `media-heading`

#### A Nested Media Object

You may even go on to nest the Media object. Without changing any of the CSS styles we have written.

```
<div class="media">  <img class="media-object" src="/pic.jpg">  <div class="media-body">    <h3 class="media-heading"> Header </h3>    <p></p>        <!--nested-->    <div class="media">    <img class="media-object" src="/pic.jpg">    <div class="media-body">        <h3 class="media-heading"> Header </h3>        <p></p>    </div>    </div><!--end nested-->  </div> </div>
```

It works!

![](https://cdn-media-1.freecodecamp.org/images/cH3o4d2UTkqB1qWCqymnvLjyGpmJ3mmEq-Ro)

Media objects nested within media objects.

#### A Unicode Media Object

It appears we are not restricted to just images.

Without changing any of the CSS styles written, you can have a unicode represent the image.

```
<div class="media">  <div class="media-object">?</div>  <div class="media-body">    <h3 class="media-heading"> Header </h3>    <p></p>  </div></div>
```

I have snugged in an emoji there.

![](https://cdn-media-1.freecodecamp.org/images/i5nrdZwTbOz3vGgZZUAwyqaG9GZEzWJSmh8i)

Media object with emoji support.

Taking away the  `img`  and replacing it with a  `div`  containing the desired unicode yields the output above.You may grab some more emoji unicodes  [here][10].

#### An HTML Entity Media Object

You may have also use  [html entities][11]  as seen below.

```
<div class="media">  <div class="media-object">☎</div>  <div class="media-body">    <h3 class="media-heading"> Header </h3>    <p></p>  </div></div>
```

The html entity used in this example is  `☎`  and you may see the result below.

![](https://cdn-media-1.freecodecamp.org/images/ssilgIfm3znqoCXzkmUXSnOuvziC5MauRQ0h)

html entity, ☎

You can view the result of these examples in this  [CodePen][12].

### Example 6: How to Build Form Elements with Flexbox

It is difficult to find any website that does not have a form or two these days.

![](https://cdn-media-1.freecodecamp.org/images/h8nCEyfprhm-MuBBUjW-vpd7W2LY6L2tdmYg)

form inputs appended and prepended with other elements

Consider the markup below:

```
<form class="form">  <input class="form__field">  <button class="form__item">…</button></form><form class="form">  <span class="form__item">…</span>  <input class="form__field"></form><form class="form">  <span class="form__item">…</span>  <input class="form__field">  <button class="form__item">…</button></form>
```

This example shows the combination of aligning input fields with buttons or spans of text. The solution again is quite easy with Flexbox.

Initiate the Flexbox formatting context:

```
.form {  display: flex}
```

Ensure the input field takes up the available space:

```
.form__field {   flex: 1}
```

Finally, you may style the appended or prepended texts and buttons whichever way you seem fit.

```
.form__item {  ... }
```

You may view the complete result of this example in this  [CodePen][13].

### Example 7: How to Build a Mobile App Layout with Flexbox

In this example, I will walk you the process the mobile app layout below:

![](https://cdn-media-1.freecodecamp.org/images/FDxWh9vQBhjQ2L6pSyb2w4QuqJvIjjuXElFF)

The mobile app layout we will build with Flexbox

However, this example is different.

I will explain the process of building the mobile layout in pseudo code, and you’ll go ahead to build it.

This will be a form of practice to get your hands  **wet**.

#### Step 1

Strip the layout off the iPhone, and we have this:

![](https://cdn-media-1.freecodecamp.org/images/cH4ifH1HxdWH9M7IpSEphw9dz7op6WJ7KM8v)

The barebones layout

#### Step 2

Define the containing body as a  `flex-container`

![](https://cdn-media-1.freecodecamp.org/images/gGlfDGRg8mSHNpD-PqZGNI9JnIzTCQiSOWrb)

Initiate the Flexbox formatting context as a flex container.

#### Step 3

By default, the  `flex-direction`  of a  `flex-container`  is set to  `row`. In this case, change it to  `column`  .

![](https://cdn-media-1.freecodecamp.org/images/C1KEFWls3---EMGS2nEiLh8pXnk6a2YOH7x0)

Change the default flex direction to have 3 child elements aka  `flex-items`

#### Step 4

Give Item 1 and 3 fixed heights such as  `height: 50px.`

#### Step 5

Item 2 must have a height that fills up the available space. Use  `flex-grow`  or the  `flex`shorthand  `flex: 1.`

#### Step 6

Finally, treat each block of content as a Media Object as seen in an earlier example.

![](https://cdn-media-1.freecodecamp.org/images/ZD4lqIbYDidmyyCu-lGXi9QXpKjaX7eOUScN)

Treat the blocks of content as media objects.

Follow the six steps above to successfully build the mobile app layout successfully.

### Want to become Pro?

Download my free CSS Grid cheat sheet, and also get two quality interactive Flexbox courses for free!

![](https://cdn-media-1.freecodecamp.org/images/Hisu3Q2Yz70DyjZSPfJ3Dr0gnZ9eB38g152g)

[Get the Free CSS Grid Cheat sheet + Two Quality Flexbox Courses for free!][14]

[Get them now][15]

  

[1]: https://payhip.com/b/YVGf
[2]: https://medium.freecodecamp.org/understanding-flexbox-everything-you-need-to-know-b4013d4dc9af
[3]: http://bit.ly/learn_css
[4]: https://codepen.io/ohansemmanuel/full/dzgLLw/
[5]: https://codepen.io/ohansemmanuel/full/Ljqdpa/
[6]: https://codepen.io/ohansemmanuel/full/xLBLLG/
[7]: https://medium.com/flexbox-and-grids/how-to-efficiently-master-the-css-grid-in-a-jiffy-585d0c213577
[8]: https://codepen.io/ohansemmanuel/full/brzJZz/
[9]: https://codepen.io/ohansemmanuel/full/brzybZ/
[10]: https://emojipedia.org/
[11]: https://www.w3schools.com/html/html_entities.asp
[12]: https://codepen.io/ohansemmanuel/full/jLJbGL/
[13]: https://codepen.io/ohansemmanuel/full/ZJPmNj/
[14]: http://eepurl.com/dcNiP1
[15]: http://eepurl.com/dcNiP1
