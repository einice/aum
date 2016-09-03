<template>
    <div class="box">
        <Badge :count="100" :max="99">
            <a href="###" class="head-example"></a>
        </Badge>
        <Switch></Switch>
        <br>
        {{{msg}}}

        <br>

        <rate :value="3" @change="state"></rate>

    </div>
</template>

<script>
    import Switch from './components/switch/Switch'
    import Badge from './components/badge/Badge'
    import Icon from './components/icon/Icon'
    import Rate from './components/rate/Rate'
    export default{
        data(){
            return {
                msg: "3D <a href='/'>Touch </a>、1200 万像素照片、4K 视频，强大功能集于一身。"
            }
        },
        methods: {
            state(val){
                console.log(val)
            }
        },
        components: {
            Switch,
            Badge,
            Icon,
            Rate
        }
    }
</script>

<style lang="scss">
@import "./scss/index.scss";
.box{
    margin: 50px;
}
.head-example {
    width: 42px;
    height: 42px;
    border-radius: 6px;
    background: #eee;
    display: inline-block;
}
</style>