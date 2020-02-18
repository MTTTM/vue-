<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" @click="show=true">
   <AsyncComponent :show="show"/>
  </div>
</template>

<script>
// @ is an alias to /src

import AsyncComponent from "./AsyncComponent"
export default {
  name: 'Home',
  components: {
    AsyncComponent
  },
  data(){
    return {
      show:false
    }
  }
}
</script>
