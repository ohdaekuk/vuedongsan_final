<template>
  <div>
    <div class="discount">
      <h4>지금 결제하면 {{this.discountPer}}% 할인</h4>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      discountPer : 30
    }
  },
  mounted() {
    setInterval(() => {
      if(this.discountPer > 0){
        this.discountPer--;
      }
    }, 1000);
  },
}
</script>

<style>

</style>