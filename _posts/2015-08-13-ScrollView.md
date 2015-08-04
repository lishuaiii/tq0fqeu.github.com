---
title: 'React Native Components ScrollView'
date: 2015-08-03 22:32:00
description: React Native文档中文翻译
---

## ScrollView
包裹了 ```ScrollView``` 的组件，同时提供了一体的触控锁定响应系统。

记住 ```ScrollView``` 必须有一个固定的高度才能工作，因为它们包含了一个不定高度的子元素在一个固定容器（通过滚动交互）。为了固定 ```ScrollView``` 的高度，要么直接设置页面高度，或者确保父页面高度是固定的。不要通过 ```{flex: 1}``` 降低页面，这样将导致错误，元素选择器一般在这里用于调试。

目前不支持其他包含的响应阻止滚动页面变成一个响应。

### 属性
#### alwaysBounceHorizontal 布尔值
> 当设置为 ```true``` 时，滚动条水平固定显示，即使内容比滚动屏幕还小。默认情况下，当 ```horizontal={true}``` 时，值为 ```true```，其他情况为 ```false```。@platform ios

#### alwaysBounceVertical 布尔值
> 当设置为 ```true``` 时，滚动条竖直固定显示，即使内容比滚动屏幕还小。默认情况下，当 ```horizontal={true}``` 时，值为 ```true```，其他情况为 ```false```。@platform ios

#### automaticallyAdjustContentInsets 布尔值
> 控制 ```iOS``` 是否让内容自适应在导航条或者工具条后面的滚动视图。默认值是 ```true```。@platform ios

#### bounces 布尔值
> 当设置为 ```true``` 时，如果内容大于滚动视图时，当滚动条到达地步，滚动体固定。当设置为 ```false``` 时，所有固定包括 ```alwaysBounce*``` 属性都无效。默认值是 ```true```。@platform ios

#### bouncesZoom 布尔值
> 当设置为 ```true``` 时，手势能驱动放大缩小到最大最小。否则放大缩小没有限制。@platform ios

#### canCancelContentTouches 布尔值
> 当设置为 ```false``` 时，一旦开始滑动，如果接触移动，不能拖动。默认值是 ```true```。@platform ios

#### centerContent 布尔值
> 当设置为 ```true``` 时，如果内容小于滚动视图，滚动视图自动将内容居中；如果内容大于滚动视图，这个属性失效。默认值是 ```false```。@platform ios

#### contentContainerStyle StyleSheetPropType(ViewStylePropTypes)
> 这些属性将应用滚动视图内容容器的所有子视图，比如：

> ```return ( <ScrollView contentContainerStyle={styles.contentContainer}> </ScrollView> ); ... var styles = StyleSheet.create({ contentContainer: { paddingVertical: 20 } });```

#### contentInset {top: number, left: number, bottom: number, right: number}
> 滚动视图内容内距。默认值为 ```{0, 0, 0, 0}```。@platform ios

#### contentOffset PointPropType
> 用于手动设置滚动开始的偏离值。默认值是 ```{x: 0, y: 0}```。@platform ios

#### decelerationRate 数字
> 一个浮点数，用于描述用户滑动滚动视图的速度。可接受的值包括：

> - Normal: 0.998(default)
  - Fast: 0.9

> @platform ios

#### directionalLockEnabled 布尔值
> 当设置为 ```true```，滚动视图将锁定只能水平或者竖直滚动在拖动的同事。默认值为 ```false```。@platform ios

#### horizontal 布尔值
> 当设置为 ```true```，滚动视图的子元素水平排列，而不是竖直排列。默认是 ```false```。

#### keyboardDismissMode 枚举['none','interactive','on-drag']
> 决定是否在拖动时摒弃键盘：

> - 'none'(default): 拖动不摒弃键盘。
  - 'on-drag': 当开始拖动时摒弃键盘。
  - 'interactive': 键盘被拖动交互式地摒弃并且与触摸同步移动；向上拖动取消了摒弃。

#### keyboardShouldPersistTaps 布尔值
> 当设置为 ```true``` 时，当键盘向上摒弃键盘时，轻击外部关注文本输入。当为真时，滚动视图不会抓取轻击，键盘不会自动摒弃。默认值为 ```false```。

#### maximumZoomScale 数字
> 最大允许缩放比例。默认值是 1.0。

#### minimumZoomScale 数字
> 最小允许缩放比例。默认值是 1.0。

#### onScroll 函数
> 在每个框架滚动过程中触发。事件频率可以通过 ```scrollEventThrottle``` 属性控制。

#### onScrollAnimationEnd 函数
> 当滚动结束时触发。@platform ios

#### pagingEnabled 布尔值
> 当设置为 ```true```，滚动视图在滚动时会在滚动视图的尺寸的倍数上停止滚动。这可以用于水平分页。默认为 ```false```。

#### removeClippedSubviews 布尔值
> 实验：当设置为 ```true``` 时，屏幕以外的子视图（它的 ```overflow``` 值是 ```hidden``` ）从本地备份的 superview 中删除。这在长列表中可以提高滚动性能。默认值是 false。

#### scrollEnabled 布尔值
> 当设置为 ```false```时，内容不能滚动。默认为 ```true```。@platform ios

#### scrollEventThrottle 数字
> 控制滚动事件在滚动时多久触发一次（单位是每秒）。更高的数字有更好的精度，有益于代码获取滚动条位置，但有可能导致滚动性能问题，这是由于事件超过了容量。默认值是0，意味着滚动事件将会在视图一滚动就触发。@platform ios

#### scrollIndicatorInsets {top: number, left: number, bottom: number, right: number}
> 滚动视图内距。一般情况下和 ```contentInset``` 保持一致。默认为 ```{0, 0, 0, 0}```。@platform ios

#### scrollsToTop 布尔值
> 当设置为 ```true``` 时，当状态条被按，滚动视图滚动到顶部。默认值是 ```true```。@platform ios

#### showsHorizontalScrollIndicator 布尔值
> 当设置为 ```true``` 时，显示水平滚动条指示器。

#### showsVerticalScrollIndicator 布尔值
> 当设置为 ```true``` 时，显示竖直滚动条指示器。

#### stickyHeaderIndices 数字数组
> 一组子视图表明确定当视图滚动时哪些子视图会停靠在屏幕的顶端。例如，传递 ```stickyHeaderIndices = {[0]}```将使得第一个子视图固定在滚动视图的顶部。此属性不支持与 ```horizontal = {true}``` 结合。

#### 属性 属性
> - [Flexbox...](https://facebook.github.io/react-native/docs/flexbox.html#proptypes)
  - [Transforms...](https://facebook.github.io/react-native/docs/transforms.html#proptypes)
  - backfaceVisibility 枚举['visible','hidden']
  - backgroundColor 字符串
  - borderBottomColor 字符串
  - borderBottomLeftRadius 数字
  - borderBottomRightRadius 数字
  - borderColor 字符串
  - borderLeftColor 字符串
  - borderRadius 数字
  - borderRightColor 数字
  - borderStyle 枚举['solid','dotted','dashed']
  - borderTopColor 字符串
  - borderTopLeftRadius 数字
  - borderTopRightRadius 数字
  - opacity 数字
  - overflow 枚举['visible','hidden']
  - shadowColor 字符串
  - shadowOffset {width: number, height: number}
  - shadowOpacity 数字
  - shadowRadius 数字

#### zoomScale 数字
> 当前滚动视图内容的规模。默认值是 1.0。

### 举例

```javascript
'use strict';

var React = require('react-native');
var {
  ScrollView,
  StyleSheet,
  View,
  Image
} = React;

exports.displayName = (undefined: ?string);
exports.title = '<ScrollView>';
exports.description = 'Component that enables scrolling through child components';
exports.examples = [
{
  title: '<ScrollView>',
  description: 'To make content scrollable, wrap it within a <ScrollView> component',
  render: function() {
    return (
      <ScrollView
        onScroll={() => { console.log('onScroll!'); }}
        scrollEventThrottle={200}
        contentInset={{top: -50}}
        style={styles.scrollView}>
        {THUMBS.map(createThumbRow)}
      </ScrollView>
    );
  }
}, {
  title: '<ScrollView> (horizontal = true)',
  description: 'You can display <ScrollView>\'s child components horizontally rather than vertically',
  render: function() {
    return (
      <ScrollView
        horizontal={true}
        contentInset={{top: -50}}
        style={[styles.scrollView, styles.horizontalScrollView]}>
        {THUMBS.map(createThumbRow)}
      </ScrollView>
    );
  }
}];

var Thumb = React.createClass({
  shouldComponentUpdate: function(nextProps, nextState) {
    return false;
  },
  render: function() {
    return (
      <View style={styles.button}>
        <Image style={styles.img} source={{uri:this.props.uri}} />
      </View>
    );
  }
});

var THUMBS = ['https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-ash3/t39.1997/p128x128/851549_767334479959628_274486868_n.png', 'https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-prn1/t39.1997/p128x128/851561_767334496626293_1958532586_n.png', 'https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-ash3/t39.1997/p128x128/851579_767334503292959_179092627_n.png', 'https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-prn1/t39.1997/p128x128/851589_767334513292958_1747022277_n.png', 'https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-prn1/t39.1997/p128x128/851563_767334559959620_1193692107_n.png', 'https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-prn1/t39.1997/p128x128/851593_767334566626286_1953955109_n.png', 'https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-prn1/t39.1997/p128x128/851591_767334523292957_797560749_n.png', 'https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-prn1/t39.1997/p128x128/851567_767334529959623_843148472_n.png', 'https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-prn1/t39.1997/p128x128/851548_767334489959627_794462220_n.png', 'https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-prn1/t39.1997/p128x128/851575_767334539959622_441598241_n.png', 'https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-ash3/t39.1997/p128x128/851573_767334549959621_534583464_n.png', 'https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-prn1/t39.1997/p128x128/851583_767334573292952_1519550680_n.png'];
THUMBS = THUMBS.concat(THUMBS); // double length of THUMBS
var createThumbRow = (uri, i) => <Thumb key={i} uri={uri} />;

var styles = StyleSheet.create({
  scrollView: {
    backgroundColor: '#6A85B1',
    height: 300,
  },
  horizontalScrollView: {
    height: 120,
  },
  containerPage: {
    height: 50,
    width: 50,
    backgroundColor: '#527FE4',
    padding: 5,
  },
  text: {
    fontSize: 20,
    color: '#888888',
    left: 80,
    top: 20,
    height: 40,
  },
  button: {
    margin: 7,
    padding: 5,
    alignItems: 'center',
    backgroundColor: '#eaeaea',
    borderRadius: 3,
  },
  buttonContents: {
    flexDirection: 'row',
    width: 64,
    height: 64,
  },
  img: {
    width: 64,
    height: 64,
  }
});
```
