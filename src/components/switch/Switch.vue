<template>
    <span class="switch" @click="toggle" :class="[checked ? 'switch-checked' : '', disabled ? 'switch-disabled' :'',small ? 'switch-small': '']">
        <span class="inner"></span>
    </span>
</template>

<script>
    export default{
        props: {
            checked: {
                type: Boolean,
                default: false
            },
            disabled: {
                type: Boolean,
                default: false
            },
            small: {
                type: Boolean,
                default: false
            }
        },
        methods: {
            toggle(){
                if (this.disabled) return;
                this.checked = !this.checked
                this.$emit('change', this.checked)
            }
        }
    }
</script>

<style lang='scss' scoped>
@import './index';
</style>