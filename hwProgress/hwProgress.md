# HwProgress
## 说明
使用进度条的目的主要出于显示效果，而非真正按照进度显示，开始加载页面时，进度条匀速增加到90%，此时如果页面未加载完毕，进度条将停止在90%的位置，页面加载完成后，进度条将瞬间到100%的位置，然后消失。

## 使用场景
网页加载需要显示加载进度条时使用
## Props
参数   | 类型 | 默认 | 说明
----- | ------ | -----  | ----
start | Boolean| true   | 是否正在加载页面
color | string | #ebebeb| 可选，进度条颜色
width | string | 100%   | 可选，进度条宽度
height| string | 3px    | 可选，进度条粗度 
## demo code
template

```
 <div>
 	<hw-progress :start="start" :color="color" :width="width" height="height"></my-progress>
 </div>
```	
script

```
 export default {
 	methods: {
 		changeStartState: function () {
 			this.start = false;
 		}
 	},
 	data () {
 		return {
 			start: true,
 			color: pink, //可选
 			width: 80%, //可选
 			height: 2px //可选
 		}
 	}
 }
``` 