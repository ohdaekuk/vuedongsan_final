<template>
  <div>

    <Modal @closeModal="closeModal" :roomData="roomData" :modalOpen="modalOpen" :check="check"/>

    <div class="menu">
      <a v-for="(a,i) in menu" :key="i">{{a}}</a>
    </div>
    <Discount v-if="showDiscount == true" />
    <br>
    <button @click="highPrice()">가격높은순</button> &nbsp;
    <button @click="lowPrice()">가격낮은순</button> &nbsp;
    <button @click="returnPrice()">가격 되돌리기</button>

    <!-- <div class="discount">
      <h4>지금 결제하면 20% 할인</h4>
    </div> -->

    <Card @openModal="openModal(); this.check = $event" v-for="(a, i) in roomData" :key="i" :roomData="a" :modalOpen="modalOpen"/>

    <!-- <div v-for="(a,i) in roomData" :key="a" @click="modalOpen = true; this.check = i">
      <img class="room-img" :src="a.image">
      <h4 >{{a.title}}</h4>
      <p>{{a.content}}</p>
      <p>{{a.price}}원</p>
    </div> -->

  </div>
</template>

<script>

import TestData from '../TestData.js'
import Modal from './components/Modal.vue'
import Card from './components/Card.vue'
import Discount from './components/Discount.vue'

export default {
  name: 'App',
  data() {
    return {
      menu : ['Home', 'Shop', 'About'],
      originData : [...TestData],
      roomData : TestData,
      modalOpen : false,
      check : 0,
      showDiscount : true
    }
  },
  methods: {
    openModal(){
      this.modalOpen = true;
    },
    closeModal(){
      this.modalOpen = false;
    },
    lowPrice(){
      this.roomData.sort(function(a, b){
        return a.price - b.price
      });
    },
    highPrice(){
      this.roomData.sort(function(a, b){
        return b.price - a.price
      })
    },
    returnPrice(){
      this.roomData = [...this.originData];
    },
  },
  components: {
    Modal,
    Card,
    Discount
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

.discount{
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
