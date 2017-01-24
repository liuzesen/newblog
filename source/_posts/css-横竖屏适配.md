---
title: '[css]横竖屏适配'
date: 2017-01-24 15:28:51
tags:
---
移动端完全支持。
参考文档：https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Media_queries#浏览器兼容性

```css
@media screen and (orientation: portrait) {
  /* 竖屏样式 */
}

@media screen and (orientation: landscape) {
  /* 横屏样式 */
}
```
<!--more-->

**bug**:安卓软键盘会导致竖屏下触发横屏的样式。可以使用以下代码解决大部分机型问题，亲测iphone 4s上会出错：

```css
@media screen and (max-aspect-ratio: 13/9) {
  /* 竖屏样式 */
}

@media screen and (min-aspect-ratio: 13/9)  {
  /* 横屏样式 */
}
```
建议使用js配合css做横竖屏样式切换，简单的就是通过resize的样式能html根dom加上**landscape**class类，从而适配样式。注意通过``document.documentElement.clientWidth``获取宽度的时候如果切换频繁会出现错乱的情况，导致样式出错，可以在页面加载的时候对这些数据进行获取，使用代码进行切换，不再使用以上代码获取。
