<template>
    <div>异步组件
        <button @click="refreshParent">点击刷新</button>
    </div>
</template>
<script>
export default {
    created(){
        console.log("异步组件初始化")
    },
     methods:{
        refreshParent(){
           this.$parent.refresh();
        }
    }
}
</script>