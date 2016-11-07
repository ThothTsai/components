# SendCode
## 说明
SendCode依赖于vux组件库中的countdown组件，在使用组件时，要保证已引入countdown组件
## 使用场景
手机获取验证码时使用
## Props
 参数   | 类型 | 默认 | 说明
----- | ------ | -----  | ----
start | Boolean|  false  | 开始倒计时
time  | string |    5    | 倒计时间长度
onCanSend | Boolean | false   | 控制按钮的disable属性
show| Boolean | false   | 显示倒计时
text| string  | '发送验证码'| 发送验证码前显示内容
sendText|string| '已发送'| 发送验证码后显示内容
#Events
  名字  |  参数  | 描述
----    | ----  | ----
on-send       | -  |点击发送验证码后触发
on-send-finish| -  |倒计时结束后触发
## demo code
template

```
 <div>
  <send-code @on-send="send" @on-send-finish="finish"    :text="text" :send-text="send-text" :start.sync="start" :time.sync="time" :no-can-send.sync="noCanSend" :c-show.sync="show"></send-code>
 <div>
 ```
 script
 
 ```
export default {
  ready() {
  },
  data () {
    return {
      start : false,
      time : 5,
      noCanSend : false,
      show: false,
      text: '发送验证码',
      send-text: '已发送'
    }
  },
  components: {
    sendCode,
  },
  methods:{
    send: function() {
      this.noCanSend = true;
    },
    finish: function() {
      this.noCanSend = false;
      this.show = false;
      this.time = 5;
      this.start = false;
    }
  }
}
```