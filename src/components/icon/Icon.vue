<template>
    <i class="iconfont" :class="['icon-'+name]"></i>
</template>

<script>
    export default{
        props: {
            name: {
                type: String,
                required: true
            }
        }
    }
</script>