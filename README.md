# wx-plugins

微信小程序插件说明文档

[![License][https://img.shields.io/badge/license-MIT-blue.svg]][https://opensource.org/licenses/mit-license.php]


## 城市列表`city-index-list`

### 属性
名称 | 类型 | 默认 | 描述
--- | --- | --- | ---
theme   | String  | `green`     | 插件主题
styles  | Object  | `{}`        | 插件自定义样式，支持：`letterBarBackground` 字母索引背景色、`letterColor` 字母默认颜色、`letterActiveColor` 字母选中的颜色、`closerBackground` 关闭按钮背景
visible | Boolean | `false`     | 是否显示


### 事件
名称 | 参数 | 描述
--- | --- | ---
onselect  | `event` | `event.detail` 为选择的城市数据，包括：`name` 城市名、`code` 城市编码


### 使用示例
注意：要先在`app.json`中配置插件的引入，然后在配置
```json
{
  "pages": [
    "pages/index/index"
  ],
  "plugins": {
    "YuanFul": {
      "version": "1.0.0",
      "provider": "wx2ca7a9c0f8d4e2b9"
    }
  }
}
```
page.wxml
```html
<city-index-list
    visible="{{cityVisible}}"
    bind:onselect="onSelectCity"
    theme="orange"
/>

<button bindtap="onClickBtn">显示</button>
```

page.js
```javascript
Page({
    data: {
        cityVisible: false
    },
    onClickBtn(){
        this.setData({
            cityVisible: true
        });
    },
    onSelectCity(e){
        let detail = e.detail;

        console.log(detail);
    }
});
```

page.json
```json
{
  "usingComponents": {
    "city-index-list": "plugin://YuanFul/city-index-list"
  }
}
```