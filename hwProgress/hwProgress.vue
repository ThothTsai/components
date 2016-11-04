<template>
    <div class="hw-progress" v-show="show">
        <div class="progress-wrap" :style="{width: width, height: height}">
            <div class="progress-bar">
                <div class="progress-inner" :style="{width: percent + '%','background': color}"></div>
            </div>
        </div>
    </div>
</template>

<style>
    .hw-progress{
        position: absolute;
        width: 100%;
    }
    .hw-progress .progress-bar {
        width: 100%;
        height: 100%;
        background-color: #ebebeb;
    }
    .hw-progress .progress-inner {
        height: 100%;
    }
</style>

<script type="text/babel">
    export default {
        data () {
            return {
                timer: null,
                percent: 0,
                show: true,
            }
        },
        components: {
        },
        props: {
            start: {
                type: Boolean,
                default: true
            },
            color: {
                type: String,
                default: '#06bebd'
            },
            width: {
                type: String,
                default: '100%'
            },
            height: {
                type: String,
                default: '3px'
            }
        },
        methods:{
            addp:function(){
                let _this  = this;

                this.timer = setInterval(function(){
                    _this.percent++
                },15)
            },
        },
        watch:{
            percent(newVal){
                let _this = this;

                if(newVal == 90){   // 如果到达90% 仍没有加载结束 就一直停在90%
                    clearInterval(this.timer)
                }else if (newVal == 100) {  // 加载结束 延迟隐藏
                    setTimeout(function(){
                        _this.show = false
                    },800)
                }
            },
            start(newVal){
                if(newVal){
                    this.addp()
                }else{  // 加载结束
                    clearInterval(this.timer)
                    this.percent = 100;
                }
            },
        },
        computed:{
        },
        ready(){
            if(this.start){
                this.addp()
            }
        }
    }
</script>