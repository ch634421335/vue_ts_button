<template>
  <div id="app">
      <Home></Home>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";
import Home from "@/Home.vue"
import { component } from 'vue/types/umd';

@Component({
  components:{
    Home
  },
})
export default class App extends Vue {

}
</script>

<style lang="stylus">
html,body 
  width 100%
  height 100%
  padding 0
  border 0
  margin 0
  box-sizing border-box
  font-size 18px
  line-height 1
  overflow hidden
*, ::before, ::after
  box-sizing inherit 
  font-size inherit 
.app
  width 100%
  width 100%
</style>
