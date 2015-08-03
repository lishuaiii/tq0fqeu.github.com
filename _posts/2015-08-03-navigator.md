---
title: 'React Native Components Navigator'
date: 2015-08-03 17:05:00
description: React Native文档中文翻译
---

## Navigator
使用 ```Navigator``` 在应用的不同场景切换。为了完成这个功能，需要提供路由对象来导航辨识每个场景，使用 ```renderScene``` 函数来根据路由渲染场景。

为了改变场景动画和手势熟悉，提供了一个 ```configureScene``` 属性去获取配置对象，用于路由。参考 ```Navigator.SceneConfigs``` 查看默认动画和更多有关场景配置的信息。

### 基本使用方式

```javascript
<Navigator
    initialRoute={ {name: 'My First Scene', index: 0}}
    renderScene={(route, navigator) =>
      <MySceneComponent
        name={route.name}
        onForward={() => {
          var nextIndex = route.index + 1;
          navigator.push({
            name: 'Scene ' + nextIndex,
            index: nextIndex,
          });
        }}
        onBack={() => {
          if (route.index > 0) {
            navigator.pop();
          }
        }}
      />
    }
  />
```

### 导航方法

如果有一个导航的参考元素，可以用多种方式触发导航：

- ```getCurrentRoutes()``` - 返回当前路由列表。
- ```jumpBack()``` - 不需要卸载当前场景跳回到上个场景。
- ```jumpForward()``` - 根据路由跳向下个场景。
- ```jumpTo(route)``` - 跳向一个指定的没有卸载的场景。
- ```push(route)``` - 导航到一个新的场景，塞入的任何场景都可以用 ```jumpForward``` 跳入。
- ```pop()``` - 回到上个场景，并卸载当前场景。
- ```replace(route)``` - 用一个新场景代替当前的场景。
- ```replaceAtIndex(route, index)``` - 用一个新场景代替当前的场景到指定位置。
- ```replacePrevious(route)``` - 用一个新场景代替上一个场景。
- ```immediatelyResetRouteStack(routeStack)``` - 用一个路由数组重置所用场景。
- ```popToRoute(route)``` - 弹出一个由它的路线指定的特定的场景。之后所有的场景将被卸载。
- ```popToTop()``` - 弹出堆栈中的第一个场景，卸载其他场景。

### 属性
#### configureScene 函数
> 这是个可选函数，用于配置场景动画和手势。将被路由触发并返回一个场景配置对象。
  ```(route) => Navigator.SceneConfigs.FloatFromRight```

#### initialRoute 对象
> 指定一个路由用于启动。路由是一个导航到指定场景的对象。如果 ```initialRouteStack``` 和 ```initialRoute``` 属性都提供了，```initialRoute``` 必须是在 ```initialRouteStack``` 里的一个路由。```initialRoute``` 默认是 ```initialRouteStack``` 的最后一项。

#### initialRouteStack 对象数组
> 提供一个初始的路由集合。如果设置了 ```initialRoute```，将会默认为一个包含了 ```initialRoute``` 的数组，否则这个选项是必要的。

#### navigationBar node
> 提供一个在各场景间共用的导航，可选。

#### navigator 对象
> 提供一个从父导航继承的导航，可选。

#### onDidFocus 函数
> @过时，使用 ```navigationContext.addListener('didfocus', callback)``` 代替。

> 当切换场景后或者在加载完场景后调用该函数。

#### onWillFocus 函数
> @过时，使用 ```navigationContext.addListener('willfocus', callback)``` 代替。

> 在切换场景前调用该函数。

#### renderScene 函数
> 用于渲染指定路由场景的必要函数。参数是路由和导航。

> ```(route, navigator) =>
  <MySceneComponent title={route.title} />```

#### sceneStyle [View#style](https://facebook.github.io/react-native/docs/view.html#style)
> 样式将被用户每个场景的容器。
