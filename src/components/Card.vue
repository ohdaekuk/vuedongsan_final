<template>
  <div>
    <div @click="$emit('openModal', roomData.id)">
      <img class="room-img" :src="roomData.image">
      <h4>{{roomData.title}}</h4>
      <p>{{roomData.content}}</p>
      <p>{{roomData.price}}원</p>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    roomData : Object,
  }
}
</script>

<style>

</style>