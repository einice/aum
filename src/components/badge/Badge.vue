<template>
    <div class="badge"><slot></slot><sup data-show="true" height="18" :class="[dot ? 'badge-dot' : 'badge-count']" :style="styles"><span v-if="!dot">{{count}}</span></sup></div>
</template>

<script>
    export default {
        props: {
            dot: {
                type: Boolean,
                default: false
            },
            count: Number,
            max: Number,
            styles: Object
        },
        ready(){
            if (this.count > this.max) {
                return this.count = this.max + '+';
            }
        }
    }
</script>

<style lang='scss' scoped>
@import './index';
</style>