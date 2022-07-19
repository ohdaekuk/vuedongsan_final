<template>
  <div>

    <div class="black-bg" v-if="modalOpen">
      <div class="white-bg">
        <img :src="roomData[this.check].image" style="width: 100%;">
        <h4>{{roomData[this.check].title}}</h4>
        <p>{{roomData[this.check].content}}</p>
        <p>{{roomData[this.check].price}}원</p>
        <button @click="modalOpen = false">닫기</button>
      </div>
    </div>

    <div class="menu">
      <a v-for="(a,i) in menu" :key="i">{{a}}</a>
    </div>

    <div v-for="(a,i) in roomData" :key="a" @click="modalOpen = true; this.check = i">
      <img class="room-img" :src="a.image">
      <h4 >{{a.title}}</h4>
      <p>{{a.content}}</p>
      <p>{{a.price}}원</p>
    </div>

  </div>
</template>

<script>

import TestData from '../TestData.js'

export default {
  name: 'App',
  data() {
    return {
      menu : ['Home', 'Shop', 'About'],
      roomData : TestData,
      modalOpen : false,
      check : 0
    }
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img{
  width: 100%;
  margin-top: 40px;
}

body {
  margin : 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}

.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
} 

</style>
