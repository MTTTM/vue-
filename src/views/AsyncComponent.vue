<template>
  <div class="home">
   <!-- <AsyncComponent v-if="show&&visible" @refresh="refresh"/> -->
   <component :is="currentView"></component>
  </div>
</template>

<script>
// @ is an alias to /src

import AsyncLoading from"./AsyncLoading"
import AsyncError from "./AsyncError"
import AsysncEmpty from "./AsyncEmpty"
const AsyncComponentX = () => ({
  // 需要加载的组件 (应该是一个 `Promise` 对象)
  component: import('./MyComponent.vue'),
  // 异步组件加载时使用的组件
  loading: AsyncLoading,
  // 加载失败时使用的组件
  error: AsyncError,
  // 展示加载时组件的延时时间。默认值是 200 (毫秒)
  delay: 100,
  // 如果提供了超时时间且组件加载也超时了，
  // 则使用加载失败时使用的组件。默认值是：`Infinity`
  timeout: 10
})
export default {
  name: 'AsyncComponent',
  props:{
      show:{
          type:Boolean,
          required:true
      }
  },
  computed:{
      currentView(){
          return this.show&&this.visible?"AsyncComponentX":"AsysncEmpty"
      }
  },
  components: {
   AsyncComponentX,
    AsysncEmpty
  },
  data(){
    return {
      visible:true
    }
  },
  methods:{
      refresh(){
          console.log("触发刷新")
          this.visible=false;
          this.$nextTick(()=>{
             // 
              console.log("刷新成功")
              setTimeout(()=>{
                  this.visible=true;
              },1000)
          })
          
      }
  }
}
</script>
