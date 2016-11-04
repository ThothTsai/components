<template>
    <div class="send-code-wrap">
        <button type="button" class="send-code-btn" :class="{'dis-code-btn' : noCanSend}" :disabled="noCanSend" @click="sendCode">
            {{sendBtnText}}
            <countdown class="count-down" slot="value" :time.sync="time" @on-finish="finish" v-show="cShow" :start.sync="start"></countdown>
        </button>
    </div>
</template>

<style lang="sass" rel="stylesheet/sass">
    .send-code-wrap
        display: inline-block
</style>

<script type="text/babel">
    import countdown from 'vux/src/components/countdown'

    export default {
        data () {
            return {
                sendBtnText: '',
                value :'',
            }
        },
        components: {
            'countdown':countdown,
        },
        props: {
            text: {
                type: String,
                default: '发送验证码'
            },
            sendText: {
                type: String,
                default: '已发送'
            },
            noCanSend: {    // 发送按钮不能点击 为 true
                type: Boolean,
                default: false,
            },
            time: {     // 倒计时时间
                type: Number,
                default: 20
            },
            cShow : {   // 倒计时显示
                type: Boolean,
                default: false,
            },
            start: {    // 开始倒计时
                type: Boolean,
                default: false,
            }
        },
        methods:{
            sendCode() {
                this.start = true;
                this.cShow = true;
                this.$emit('on-send')
            },
            finish () {
                this.$emit('on-send-finish')
            }
        },
        watch:{
            noCanSend (newVal) {
                console.log(newVal)
                if(newVal) {
                    this.sendBtnText = this.sendText;
                }else {
                    this.sendBtnText = this.text;
                }
            },
        },
        computed:{
        },
        ready(){
            this.sendBtnText = this.text;
        }
    }
</script>