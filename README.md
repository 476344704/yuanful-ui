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
      "version": "1.0.1",
      "provider": "wx2ca7a9c0f8d4e2b9"
    }
  }
}
```

## 插件目录
* [城市选择列表 city-index-list](#city-index-list)
* [搜索组件 searchbar](#searchbar)



## 插件说明
#### 插件主题颜色值
* <img width="10px" height="10px" src="theme/blue.png" /> blue `#03a9f4`
* <img width="10px" height="10px" src="theme/orange.png" /> orange `#f19149`
* <img width="10px" height="10px" src="theme/red.png" /> red `#f44336`
* <img width="10px" height="10px" src="theme/green.png" /> green `#009688`

<details>
<summary id="city-index-list">
城市选择列表 city-index-list
</summary>

  ### 预览
  <div>
    <img width="40%" src="preview/city-index-list.png" />
  </div>

  ### 属性
  名称 | 类型 | 默认 | 描述
  --- | --- | --- | ---
  theme   | String  | `blue`     | 插件主题<br/>支持：`orange`、`red`、`blue`、`green`
  styles  | Object  | `{}`        | 插件自定义样式<br/>支持：`letterBarBackground` 字母索引背景色、`letterColor` 字母默认颜色、`letterActiveColor` 字母选中的颜色、`closerBackground` 关闭按钮背景
  visible | Boolean | `false`     | 是否显示

  ### 事件
  名称 | 参数 | 描述
  --- | --- | ---
  select  | `event` | 选择城市的回调，`event.detail` 为选择的城市数据，包括：`name` 城市名、`code` 城市编码

  ### 使用
  page.wxml
  ```html
  <city-index-list
      theme="orange"
      visible="{{cityVisible}}"
      styles="{{cityStyles}}"
      bind:select="onSelectCity"
  />

  <button bind:tap="onClickBtn">显示</button>
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
<br/>[⬆ 返回目录](#插件目录)
</details>


<details>
<summary id="searchbar">
  搜索组件 searchbar
</summary>

  ### 预览
  <div>
    <img width="40%" src="preview/searchbar.png" />
  </div>

  ### 属性
  名称 | 类型 | 默认 | 描述
  --- | --- | --- | ---
  theme   | String  | `blue`     | 插件主题<br/>支持：`orange`、`red`、`blue`、`green`
  visible | Boolean | `false`     | 是否显示
  placeholder | String | `请输入关键字`     | 输入框默认占位文字
  search-value | String | ``     | 输入框默认值，默认为空
  clear-confirm | Boolean | `true`     | 点击清空是否弹出二次确认框
  confirm-config | Object | `{ content: '确定要清空吗？' }`     | 清空时二次确认弹窗配置，与`wx.showModal`参数一致

  ### 事件
  名称 | 参数 | 描述
  --- | --- | ---
  search  | `event` | 搜索的回调，`event.detail.text` 为搜索的文字
  cancel  | `event` | 取消的回调

  ### 使用
  page.wxml
  ```html
  <searchbar
    visible="{{searchbarVisible}}"
    search-value="测试"
    confirm-config="{{confirmConfig}}"
    clear-confirm="{{true}}"
    bind:search="onSearch"
  />

  <button bind:tap="onClickBtn">显示</button>
  ```

  page.js
  ```javascript
    Page({
      data: {
        confirmConfig: {
          content: '确定要清空内容吗？'
        }
      },
      onClickBtn() {
          this.setData({
              searchbarVisible: true
          });
      },
      onSearch(e) {
          let detail = e.detail;

          console.log(detail);
      }
    });
  ```

  page.json
  ```json
  {
    "usingComponents": {
      "searchbar": "plugin://YuanFul/searchbar"
    }
  }
  ```

<br/>[⬆ 返回目录](#插件目录)
</details>