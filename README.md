# wx-plugins

**wx-plugins**是一套可添加到小程序内直接使用的功能组件，无需重复开发，为用户提供更丰富的服务。

![yuanful-wx-plugins](https://img.shields.io/badge/license-MIT-blue.svg)


## 插件安装
在`app.json`中配置插件的引入
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

## 插件目录
* [城市选择列表 `city-index-list`](#城市选择列表-city-index-list)



## 插件说明
<details>
<summary id="城市选择列表-city-index-list">
  城市选择列表 `city-index-list`
</summary>

  ### 预览
  <div>
    <img width="40%" src="preview/city-index-list.png" alt="yuanful-wx-plugins" />
  </div>

  ### 属性
  名称 | 类型 | 默认 | 描述
  --- | --- | --- | ---
  theme   | String  | `green`     | 插件主题，目前有：`orange`颜色值`#f19149`、`red`颜色值`#f44336`、`blue`颜色值`#03a9f4`、`green`颜色值`#009688`
  styles  | Object  | `{}`        | 插件自定义样式，支持：`letterBarBackground` 字母索引背景色、`letterColor` 字母默认颜色、`letterActiveColor` 字母选中的颜色、`closerBackground` 关闭按钮背景
  visible | Boolean | `false`     | 是否显示

  ### 事件
  名称 | 参数 | 描述
  --- | --- | ---
  onselect  | `event` | `event.detail` 为选择的城市数据，包括：`name` 城市名、`code` 城市编码

  ### 使用
  page.wxml
  ```html
  <city-index-list
      theme="orange"
      visible="{{cityVisible}}"
      styles="{{cityStyles}}"
      bind:onselect="onSelectCity"
  />

  <button bindtap="onClickBtn">显示</button>
  ```

  page.js
  ```javascript
  Page({
      data: {
          cityVisible: false,
          cityStyles: {
              letterColor: '#fff'
          }
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

</details>