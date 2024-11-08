<template>

  <div class="black-bg" v-if="modalIsOpen == true">
    <div class="white-bg">
      <img :src="oneroomdata[clickedNum].image" :alt="oneroomdata[clickedNum].title" class="modal-image">
      <h4>{{oneroomdata[clickedNum].title}}</h4>
      <p>{{oneroomdata[clickedNum].content}}</p>
      <p>현재 가격 : {{ oneroomdata[clickedNum].price }}원</p>
      <button @click="modalIsOpen = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="a in menu" :key="a">{{ a }}</a>
  </div>

  <div v-if="1 == 1">
    안녕하세요!!
  </div>
  <div v-else>
    안녕히가세요!!
  </div>

  <div v-for="(room, i) in oneroomdata" :key="i">
    <img :src="room.image" :alt="room.title" class="room-img">
    <h4 @click="modalIsOpen = true; clickedNum = i">{{ room.title }}</h4>
    <p>{{ room.price }} 원</p>
  </div>
</template>

<script>

import data from './assets/oneroom';

export default {
  name: 'App',
  data() {
    return {
      clickedNum : 0,
      oneroomdata : data,
      menu : ['Home', 'Shop', 'About'],
      modalIsOpen : false,
    }
  },
  components: {
  }
}
</script>

<style>
/* 여기서부터 모달창임 */
body{
  margin : 0
}
div {
  box-sizing: border-box;
}
.black-bg{
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}
.white-bg{
  width: 80%;
  max-width: 500px;
  background: white;
  border-radius: 8px;
  padding: 20px;
  position: relative;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}
.modal-image{
  width: 70%;
}
/* 여기까지 모달창임 */

.room-img{
  width: 100%;
  margin-top: 40px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu{
  background: darkblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color: white;
  padding: 10px;
}
</style>
