# react-google-svg-icon

這是針對 [react] 所開發的 module，所有 svg 的 來源為 [material-design-icons]，你可以在 [Material icons] 看到所有的 icon 列表。

### 前言
分析了原本的 [material-design-icons] 之後，將其分成 4 個 size：
* xs: 18px, 共有 141 個 icon
* s:  24px, 共有 740 個 icon
* md: 36px, 共有 22 個 icon
* lg: 48px, 共有 739 個 icon

其中需要注意的地方，在原本的 icon 裡，有幾個 icon 是不符合上面的大小，這幾個 icon 為：
* device/ic_signal_wifi_statusbar_1_bar_26x24px.svg
* device/ic_signal_wifi_statusbar_2_bar_26x24px.svg
* device/ic_signal_wifi_statusbar_3_bar_26x24px.svg
* device/ic_signal_wifi_statusbar_4_bar_26x24px.svg
* device/ic_signal_wifi_statusbar_connected_no_internet_1_26x24px.svg
* device/ic_signal_wifi_statusbar_connected_no_internet_26x24px.svg
* device/ic_signal_wifi_statusbar_connected_no_internet_2_26x24px.svg
* device/ic_signal_wifi_statusbar_connected_no_internet_3_26x24px.svg
* device/ic_signal_wifi_statusbar_connected_no_internet_4_26x24px.svg
* device/ic_signal_wifi_statusbar_not_connected_26x24px.svg
* device/ic_signal_wifi_statusbar_null_26x24px.svg

因此我並沒有將這幾個 icon 加入這個 module 裡，未來若有需要，可能會再更新。


### 安裝
此 module 加入了 npm，所以安裝過程如下

```sh
$ npm install react-google-svg-icon
```

### 使用
```sh
var React = require('react'),
var icon = require('react-google-svg-icon');
var SvgIcon = icon.s;

var Main = React.createClass({
    render : function(){
        return (
            <div>
            <SvgIcon name={'account_box'} style={{fill:'red'}}/>
            </div>            
        );
    }
});
React.render(<Handler/>, document.getElementById("main-app"));
```
`var SvgIcon = icon.s;` 表式是要使用 24px 大小的 icon 

`<SvgIcon name={'account_box'} style={{fill:'red'}}/>`，name 的名稱可以在 [Material icons] 裡找到，也請注意，若是在 [Material icons] 找到的 name 有空白的話，需要加入 "_" 下底線，而 style 可以更換 svg 的顏色以及背景顏色。

例如
```sh
<SvgIcon 
    name={'account_box'} 
    style={{
        fill: 'red'
        background: 'green'
    }}
/>
```

### 其他
若是直接使用 `var icon = require('react-google-svg-icon');` 在使用 webpack 打包時，會將所有的 icon size 一起打包起來，這會造成最後 complie 後的 js 龐大，你可以改用下面的方式，只取你需要的大小就好

```sh
var SvgIcon = require('react-google-svg-icon/dist/24px');
var Main = React.createClass({
    render : function(){
        return (
            <div>
            <SvgIcon name={'account_box'} style={{fill:'red'}}/>
            </div>            
        );
    }
});
React.render(<Handler/>, document.getElementById("main-app"));
```
這樣 js 的 size 可以減少不小

[react]:https://facebook.github.io/react/
[material-design-icons]:https://github.com/google/material-design-icons
[Material icons]:https://www.google.com/design/icons/
