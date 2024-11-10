<template>
  <div>
    <img :src="room.image" :alt="room.title" class="room-img">
    <h4 @click="openModal">{{ room.title }}</h4>
    <p>{{ room.price }} 원</p>
  </div>
</template>

<script>
export default {
    props : {
        room : Object,
    },
    methods : {
        openModal(){
            this.$emit('openModal', this.room.id)
        }
    }
}
</script>

<style>

</style>