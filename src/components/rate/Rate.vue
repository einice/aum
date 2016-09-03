<template>
    <ul class="rate" :class="{'rate-disabled': disabled}" @mouseleave="onMouseLeave" v-el:rate>
        <star v-for="(i, item) of count"
            :index="i" 
            :value="hoverValue === undefined ? this.value : hoverValue"
            :allow-half="allow"
            :disabled="disabled"
            :hover="handleHover"
            :click="handleClick"
            ></star>
    </ul>
</template>

<script>
    import Star from './Star'
    export default{
        props: {
            count:{
                type: Number,
                default: 5
            },
            disabled: {
                type: Boolean,
                default: false
            },
            value: {
                type: Number,
                default: 0
            },
            allow: {
                type:Boolean,
                default: false
            },
            change: {
                type: Function,
                default: ()=>{}
            }
        },
        data(){
            return {
                hoverValue: undefined
            }
        },
        methods: {
            handleClick(event, index){
              this.value = this.getStarValue(index, event.pageX);
              this.onMouseLeave()
              this.$emit('change', this.value)
            },
            handleHover(event, index){
                this.hoverValue = this.getStarValue(index, event.pageX);
            },
            getStarValue(index, x){
                let value = index + 1;
                if (this.allow) {
                    let el = this.$els.rate
                    const leftEdge = el.offsetLeft;
                    const width = getOffsetLeft(this.getStarDOM(1)) - leftEdge;
                    if ((x - leftEdge - width * index) < width / 2) {
                        value -= 0.5;
                    }
                }
                return value;
            },
            onMouseLeave(){
                if (this.disabled) return;
                this.hoverValue = undefined;
            },
            getStarDOM(index) {
                let el = this.$els.rate;
                return el.children[index];
            },
        },
        components: {
            Star
        }
    }
</script>

<style lang='less' scoped>
@import "./index";
</style>