---
title:  "React Native Components ActivityIndicatorIOS"
date:   2015-07-28 08:28:00
description: React Native文档中文翻译
---

## ActivityIndicatorIOS
### 属性
#### animating 布尔值
> 决定是否展现指示版（indicator），默认为真。

#### color 字符串
> 浮层(spinner)的前置背景色，默认为灰色。

#### hidesWhenStopped 布尔值
> 当没有动作时隐藏指示版（indicator），默认为真。

#### onLayout 函数
> 布局加载或者变化时触发，
```
{nativeEvent: { layout: {x, y, width, height}}}
```

#### size 枚举 ['small', 'large']
> 指示版（indicator）尺寸，Small的高度是20，Large的高度是36。

### 举例
```javascript
'use strict';

var React = require('react-native');
var {
  ActivityIndicatorIOS,
  StyleSheet,
  View,
} = React;
var TimerMixin = require('react-timer-mixin');

var ToggleAnimatingActivityIndicator = React.createClass({
  mixins: [TimerMixin],

  getInitialState: function() {
    return {
      animating: true,
    };
  },

  setToggleTimeout: function() {
    this.setTimeout(
      () => {
        this.setState({animating: !this.state.animating});
        this.setToggleTimeout();
      },
      1200
    );
  },

  componentDidMount: function() {
    this.setToggleTimeout();
  },

  render: function() {
    return (
      <ActivityIndicatorIOS
        animating={this.state.animating}
        style={[styles.centering, {height: 80}]}
        size="large"
      />
    );
  }
});

exports.displayName = (undefined: ?string);
exports.framework = 'React';
exports.title = '<ActivityIndicatorIOS>';
exports.description = 'Animated loading indicators.';

exports.examples = [
  {
    title: 'Default (small, white)',
    render: function() {
      return (
        <ActivityIndicatorIOS
          style={[styles.centering, styles.gray, {height: 40}]}
          color="white"
          />
      );
    }
  },
  {
    title: 'Gray',
    render: function() {
      return (
        <View>
          <ActivityIndicatorIOS
            style={[styles.centering, {height: 40}]}
          />
          <ActivityIndicatorIOS
            style={[styles.centering, {backgroundColor: '#eeeeee', height: 40}]}
          />
        </View>
      );
    }
  },
  {
    title: 'Custom colors',
    render: function() {
      return (
        <View style={styles.horizontal}>
          <ActivityIndicatorIOS color="#0000ff" />
          <ActivityIndicatorIOS color="#aa00aa" />
          <ActivityIndicatorIOS color="#aa3300" />
          <ActivityIndicatorIOS color="#00aa00" />
        </View>
      );
    }
  },
  {
    title: 'Large',
    render: function() {
      return (
        <ActivityIndicatorIOS
          style={[styles.centering, styles.gray, {height: 80}]}
          color="white"
          size="large"
        />
      );
    }
  },
  {
    title: 'Large, custom colors',
    render: function() {
      return (
        <View style={styles.horizontal}>
          <ActivityIndicatorIOS
            size="large"
            color="#0000ff"
          />
          <ActivityIndicatorIOS
            size="large"
            color="#aa00aa"
          />
          <ActivityIndicatorIOS
            size="large"
            color="#aa3300"
          />
          <ActivityIndicatorIOS
            size="large"
            color="#00aa00"
          />
        </View>
      );
    }
  },
  {
    title: 'Start/stop',
    render: function(): ReactElement {
      return <ToggleAnimatingActivityIndicator />;
    }
  },
];

var styles = StyleSheet.create({
  centering: {
    alignItems: 'center',
    justifyContent: 'center',
  },
  gray: {
    backgroundColor: '#cccccc',
  },
  horizontal: {
    flexDirection: 'row',
    justifyContent: 'space-around',
  },
});
```

