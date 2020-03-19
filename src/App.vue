<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
  provide(){
    return{
      replace:this.replace
    }
  },
  methods:{
    replace(key,val){
      let apple=JSON.stringify(this.$route.query);
      let banner=JSON.parse(apple);//浅拷贝变深拷贝
      banner[key]=val;
      this.$router.push({
        path:this.$route.path,
        query:banner
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
