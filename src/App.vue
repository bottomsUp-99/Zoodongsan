<template>

  <transition name="fade">
    <Modal @modalClose="modalIsOpen = false" :clickedNum="clickedNum" :oneroomdata="oneroomdata" :modalIsOpen="modalIsOpen" />
  </transition>
  <!-- <div class="start" :class="{end : modalIsOpen}">
    <Modal @modalClose="modalIsOpen = false" :clickedNum="clickedNum" :oneroomdata="oneroomdata" :modalIsOpen="modalIsOpen" />
  </div> -->


  <div class="menu">
    <a v-for="a in menu" :key="a">{{ a }}</a>
  </div>

  <Discount v-if="showDiscount == true"/>

  <button @click="priceSort">가격순 정렬</button>
  <button @click="titleSort">이름순 정렬</button>
  <button @click="sortBack">되돌리기</button>

  <div v-if="1 == 1">
    안녕하세요!!
  </div>
  <div v-else>
    안녕히가세요!!
  </div>

  <Card @openModal="modalIsOpen = true; clickedNum = $event" v-for="(room, i) in oneroomdata" :key="room" :room="oneroomdata[i]"/>


</template>

<script>

import data from './assets/oneroom';
import Discount from './Discount.vue';
import Modal from './Modal.vue'
import Card from './Card.vue'


export default {
  name: 'App',
  data() {
    return {
      originOfOneroomdate : [...data],
      // [...data]는 array에 개별 복사본을 저장하는겨
      clickedNum : 0,
      oneroomdata : data,
      menu : ['Home', 'Shop', 'About'],
      modalIsOpen : false,
      showDiscount : true,
    }
  },
  methods : {
    priceSort(){
      this.oneroomdata.sort(function(a,b){
        return a.price - b.price;
      })
    },
    titleSort(){
      this.oneroomdata.sort(function(a,b){
        return a.title.localeCompare(b.title);
      })
    },
    sortBack(){
      this.oneroomdata = [...this.originOfOneroomdate];
    },
  },
  mounted(){
    setTimeout(()=>{
      this.showDiscount = false;
    }, 2000);
  },
  components: {
    Discount,
    Modal,
    Card,
  }
}
</script>

<style>
/* 여기서부터 모달창임 */

/* .start{
  opacity: 0;
  transition: all 1s;
}
.end{
  opacity: 1;
} */
/* 이건 div로 묶어서 모달창 애니메이션 효과주는것 */
/* 위랑 아래랑 똑같은 효과임 */
.fade-enter-from{
  opacity: 0;
}
.fade-enter-active{
  transition: all 1s;
}
.fade-enter-to{
  opacity: 1;
}

/* .fade-enter-from{
  transform: translateY(-1000px);
}
.fade-enter-active{
  transition: all 1s;
}
.fade-enter-to{
  transform: translateY(0px);
} */

.fade-leave-from{
  opacity: 1;
}
.fade-leave-active{
  transition: all 1s;
}
.fade-leave-to{
  opacity: 0;
}

body{
  margin : 0
}
div {
  box-sizing: border-box;
}
.discount{
  background: #eee;
  padding: 10px;
  margin: 10px;
  margin-top: 60px;
  border-radius: 5px;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
}

.white-bg {
  width: 80%;
  max-width: 500px;
  background: white;
  border-radius: 8px;
  padding: 20px;
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
/* .menu{
  background: darkblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color: white;
  padding: 10px;
} */
.menu {
  background: darkblue;
  padding: 15px;
  border-radius: 5px;
  color: white;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: center;
  z-index: 10;
}

.menu a {
  color: white;
  padding: 10px;
  margin: 0 5px;
}
</style>
