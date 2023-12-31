# css-animation
﻿ <h2>流光按钮</h2>

博客地址：(https://zhuanlan.zhihu.com/p/649665010)

本文将带您一步步学习，如何用CSS制作一个令人赞叹的流光按钮，无需专业设计技能，只需一些基本的CSS知识，您就能轻松地为您的项目创造一个独特的视觉效果。话不多说，上才艺，全部代码在文章末尾。

![image](https://pic1.zhimg.com/v2-d77b4023a2590321a4bbf615f7bf2b94_b.webp)

<font color="#nsdlkdsssddfmk">1.首先设计一个最基本的按钮，将其置于屏幕正中心，并将其设置背景、高宽、文字颜色等</font>

> 注意css的注释只能使用/* xxx */，避免写成//或者<!-- <!--->-->

![image](https://pic2.zhimg.com/80/v2-74e30ea41446e055d18c0b399c0319a5_720w.webp)

效果如下：

![image](https://pic4.zhimg.com/80/v2-a919d2fe8be736d752a6d140453f4773_720w.webp)

<font color="#nsdlkdsssddfmk">2.如何给元素加入流动效果呢？</font>

为了实现流动的效果，首先需要将 background-size 放大到原来的4倍。随后，我们需要考虑何时触发流动效果。通常情况下，当鼠标悬停在按钮元素上时，流动效果会被触发。为了实现这一点，我们可以借助伪类 :hover。

> 为什么要将背景图片大小放大为原来的4倍呢？这是因为默认情况下，背景图片的尺寸是根据其原始大小来渲染的，而不会随着按钮的大小和动画而改变。当背景图片被放大时，在背景图片移动的过程中，你能够更清楚地看到背景图片的变化，从而更好地呈现流动效果。

* 在a{}加入以下内容

![image](https://pic1.zhimg.com/80/v2-c77bd03d1377c353b5a4b85166785e14_720w.webp)

* 定义动画帧
* 
![image](https://pic3.zhimg.com/80/v2-e7a12bc87317407162a4db10c47e32be_720w.webp)

> 在 @keyframes 规则中的 100% 关键帧，背景图片的 background-position 被设置为 -400%
0。这会使背景图片的初始位置从右侧超出按钮边界，然后在动画过程中移动到按钮内部，创造出一个从右往左的流动效果。
这里的 -400% 意味着将背景图片的位置向左偏移，移动的距离相当于按钮宽度的4倍。这样在动画的最终状态（100%
关键帧），背景图片会位于按钮的最左侧，形成流动效果。

按钮位置不会发生改变，整个起始-终点就如同下面这张图所示

![image](https://pic1.zhimg.com/80/v2-ae2b2e7cb6017ff60be4f5569f9cec54_720w.webp)

本质上，这种效果通过放大背景图片并移动它的位置，给人一种流动的视觉效果，仿佛背景在按钮内部流动一样。

<font color="#nsdlkdsssddfmk">3.虚幻按钮边界</font>

要实现虚幻按钮边界效果，首先需要在按钮上添加一个边框，其大小距离按钮元素的外边距5px。值得注意的是，务必为边框设置 position:absolute 属性，以使其脱离正常的文档流，从而与按钮和页面主体进行叠加（当然，后续需要确保按钮显示在最上方）。

![image](https://pic4.zhimg.com/80/v2-9f508d50039b9cb21e05dc56d927ccc3_720w.webp)

![image](https://pic2.zhimg.com/80/v2-ccbfd6833857616371ec31f66031ed99_720w.webp)

将内容模糊化，并设置一些基本属性。在a:before:{}加入以下内容

![image](https://pic2.zhimg.com/80/v2-7fbae6d1d44aa1e9f73bbc1c8bc670f9_720w.webp)

![image](https://pic2.zhimg.com/80/v2-a90d22200d17388e780e845df4936bc9_720w.webp)

此时会发现a的伪元素的层级大于a元素的层级，导致按钮被覆盖了。【请注意，只有在元素脱离正常的文档流后，它们才能在 z
轴上叠加。在这种情况下，屏幕到我们眼睛的方向被视为 z 轴，而正常的文档流则发生在 x*y
平面上】所以为了解决覆盖问题，需要为a和a的伪元素设置z-index值，使a的的z-index大于a的伪元素的z-index，z-index越大，越显示在上层。

> 在a{}中加入z-index: 1; 在a:before{}中加入z-index: -1;

此时效果如下所示：

![image](https://pic4.zhimg.com/v2-efd40b5d3c4ca2d58304942b951618c3_b.jpg)

接下来也要将伪元素的样式发生流动

![image](https://pic3.zhimg.com/80/v2-f1fcd1348cb2669243a9b06ec8c1ab2e_720w.webp)

> 注意在 CSS 中，a:hover:before 和 a:before:hover 的语法是不同的，并且会产生不同的效果。

1. a:hover:before： 这种写法表示在链接 a 元素上悬停时，选择其伪元素 ::before
来应用样式。也就是说，在鼠标悬停在链接上时，会触发 ::before 伪元素的样式。
2. a:before:hover： 这种写法表示选择链接 a 元素的伪元素 ::before，然后在伪元素上悬停时应用样式。实际上，这种写法是无效的，因为伪元素本身并不具有交互性，所以不会在伪元素上触发悬停效果。

<font color="#nsdlkdsssddfmk">4.最终效果</font>

![image](https://pic1.zhimg.com/v2-d77b4023a2590321a4bbf615f7bf2b94_b.jpg)
