<template>
  <div class="black-bg" v-if="modalIsOpen == true">
    <div class="white-bg">
      <button @click="modalIsOpen = false">닫기</button>
      <h4>상세페이지</h4>
      <p>상세내용</p>
    </div>
  </div>

  <div class="menu">
    <a v-for="a in menu" :key="a">{{ a }}</a>
  </div>
  
  <div>
    <img src="./assets/room0.jpg" class="room-img">
    <h4>{{products[0]}}</h4>
    <p>50 만원</p>
    <button @click="increase(0)">허위매물신고</button> <span>신고수 : {{count[0]}}</span>
  </div>
  <div>
    <img src="./assets/room1.jpg" class="room-img">
    <h4>{{products[1]}}</h4>
    <p>가격은 아무거나</p>
    <button @click="increase(1)">허위매물신고</button> <span>신고 수 : {{ count[1] }}</span>
  </div>
  <div>
    <img src="./assets/room2.jpg" class="room-img">
    <h4>{{ products[2] }}</h4>
    <p>가격은 아무거나</p>
    <button @click="increase(2)">허위매물신고</button> <span>신고 수 : {{ count[2] }}</span>
  </div>

  <hr>
  <hr>

  <div v-for="(room, i) in products" :key="i">
    <img :src="img[i]" :alt="products[i]" class="room-img">
    <h4 @click="modalIsOpen = true">{{ room }}</h4>
    <p>{{ price[i] }} 만원</p>
    <button @click="increase(i)">허위매물 신고</button> <span>신고 수 : {{ count[i] }}</span>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      menu : ['Home', 'Shop', 'About'],
      products : ['역삼동 원룸', '천호동원룸', '마포구원룸'],
      price : [10, 20, 30],
      count : [0 ,0, 0],
      img : [require('./assets/room0.jpg'), require('./assets/room1.jpg'), require('./assets/room2.jpg')],
      modalIsOpen : false,
    }
  },
  methods: {
    increase(a){
      this.count[a] += 1;
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
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
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
