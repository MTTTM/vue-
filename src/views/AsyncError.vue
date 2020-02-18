<template>
    <div>异常
        <div>
             <button @click="refreshParent">点击刷新</button>
        </div>
    </div>
</template>
<script>
export default {
    name:"AsyncError",
    methods:{
        refreshParent(){
           this.$parent.refresh();
        }
    }
}
</script>