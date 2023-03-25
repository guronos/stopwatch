<template>
<div class="main">
<div class="stop-watch" v-for="i in quantityBlocks" :key="i"><StopWatch /></div>
<!-- <div class="stop-watch"><StopWatch /></div> -->
<div class="adding-panel" @click="quantityBlocks+=1">
  <div class="minus"></div>
  <div class="plus"></div>
</div>
</div>
</template>

<script>
import StopWatch from './components/StopWatch'
export default {
  name: 'App',
  components: {
    StopWatch
  }, data () {
    return {
      quantityBlocks : 2
    }
  }
}
</script>

<style>
@import url('https://fonts.cdnfonts.com/css/gotham-pro');
* {
  margin: 0;
}
body {
  background: #494444;
}
#app {
  font-family: 'Gotham Pro', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #f5f6f7;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
.main {
display: flex;
max-width: 830px;
flex-wrap: wrap;
}
.stop-watch {
margin: 0 0 45px 50px;
}
.adding-panel {
background: #696969;
width: 225px;
height: 120px;
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;
margin: 0 0 45px 50px;
}
.minus {
width: 3px;
height: 20px;
background: #fff;
transform: rotate(90deg);
margin-top: 10px;
}
.plus {
width: 3px;
height: 20px;
background: #fff;
position: relative;
top: -19px;
}
@media (max-width : 1024px) {
.main {
width: 550px;
}
}
@media (max-width : 768px) {
.main {
width: 320px;
}
}
</style>
