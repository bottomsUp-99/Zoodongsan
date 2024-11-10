<template>
  <div class="black-bg" v-if="modalIsOpen == true">
    <div class="white-bg">
      <img :src="oneroomdata[clickedNum].image" :alt="oneroomdata[clickedNum].title" class="modal-image">
      <h4>{{oneroomdata[clickedNum].title}}</h4>
      <p>{{oneroomdata[clickedNum].content}}</p>
      <!-- <input @input="month = $event.target.value"> -->
      <!-- <input v-model="month"> -->
      <!-- 둘이 똑같은 기능을 함 -->
      <input v-model="month">
      <p>{{ month }}개월 선택했을 경우의 값 : {{ oneroomdata[clickedNum].price * month }}원</p>
      <button @click="$emit('modalClose')">닫기</button>
      <Discount/>
    </div>
  </div>
</template>

<script>
export default {
    name : 'Modal',
    data(){
        return{
          month : 1,
        }
    },
    watch : {
        month(a){
            if(a >= 13){
              alert('13개월 이상은 계약하실 수 없습니다!!');
            }
            if(isNaN(a) == true){
              alert('문자는 입력하실 수 없습니다!!');
              this.month = 1;
            }
        },
    },
    props : {
        clickedNum : Number,
        oneroomdata : Array,
        modalIsOpen : Boolean,
    },
    
}
</script>

<style>

</style>