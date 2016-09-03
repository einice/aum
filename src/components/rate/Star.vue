<template>
    <li class="rate-star" :class="[onClass]" @click="onClick" @mousemove="onHover">
        <div class="rate-star-content"></div>
    </li>
</template>

<script>
    export default{
        props: {
            value: Number,
            index: Number,
            allowHalf: Boolean,
            disabled: Boolean,
            hover: Function,
            click: Function
        },
        computed: {
            onClass(){
                const starValue = this.index + 1;
                if (this.allowHalf && this.value + 0.5 === starValue) {
                    return 'rate-star-half rate-star-active';
                }
                return starValue <= this.value ? 'rate-star-full' : 'rate-star-zero';
            }
        },
        methods: {
            onHover(e){
                if (this.disabled) return null;
                this.hover(e, this.index)
            },
            onClick(e){
                if (this.disabled) return null;
                this.click(e, this.index)
            }
        }
    }
</script>

<style lang='less' scoped>
@import "./index.less";
</style>