<template>
  <div>
    <div class="black-bg" v-if="modalOpen">
      <div class="white-bg" @mouseleave="closeService()">
        <img :src="roomData[this.check].image" style="width: 100%;">
        <h4>{{roomData[this.check].title}}</h4>
        <p>{{roomData[this.check].content}}</p>
        <input v-model.number="month">
        <p>{{month}}개월 선택함 : {{month * roomData[this.check].price}}원</p>
        <button @click="closeService()">닫기</button>
      </div>
    </div>
  </div>
</template>

<script>
import Discount from './Discount.vue';
export default {
  data() {
    return {
      month : 0
    }
  },
  props: {
      roomData: Array,
      modalOpen: Boolean,
      check: Number
  },
  components: {
      Discount 
  },
  methods: {
    closeService(){
      this.$emit('closeModal');
      this.month = 0;
    }
  },
  beforeUpdate() {
    if(this.month === 2 || this.month === 1){
      alert("3 이상의 수를 적어주세욤");
      this.month = 3;
    }
  },
  watch: {
    month(data){
      if(data > 12){
        alert("13 미만의 숫자를 입력해주세요.");
        this.month = 1;
      }

      if(isNaN(data)){
        alert("숫자만 입력해주세요.")
        this.month = 1;
      }
    }
  }
}
</script>

<style>

</style>