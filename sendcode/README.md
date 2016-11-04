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
## demo code
template

```
 <div>
  <send-code @on-send="send" @on-send-finish="finish"    text="获取验证码" send-text="发完啦" :start.sync="start" :time.sync="time" :no-can-send.sync="noCanSend" :c-show.sync="show"></send-code>
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