<template>
    <div class="header">
        <a v-for="(a ,i) in menus" :key="i">asds</a>
    </div>
    <button @click="sortPrice">가격 순정렬</button>
    <button @click="sortPrice2">가격 되돌리기</button>
    <ul>
        <li @openModal="$event" v-for="(listD ,i) in list" :key="i">
            <img :src="listD.image">
            <h4 state = i><em>{{i+1}}.</em>{{listD.title}}</h4>
            <p>{{listD.price *month}}</p>
            <span>{{month }}개월 선택함 : {{listD.content}}</span>
            <input v-model.number="month">
        </li>
    </ul>
    <div class="discount">
        <p>지금 구매하면 20% 할인</p>
    </div>
    <discount></discount>
    <modal :list = "list" :modalWindow = "modalWindow"></modal>
</template>

<script>
import listData from './assets/list.js';
import discountData from './components/discount-comp.vue';
import modaltData from './components/modal-div.vue';

export default {
    name: 'App',
    data(){
        return {
            month : 0,
            list : listData,
            modalWindow : true,
            menus : ['home' , 'product' , 'about'],
            product : listData,
            price : ['60' , '70', '80'],
            like : [0 , 0 , 0],
            listorigin : [...listData],
        }
    },
    watch :{
        month(a){
            if(a > 13){
                alert("씨이발")
                return a 
            }
            if(isNaN(a)){
                alert("문자다")
                a = this.month
            }
        }
    },
    methods : {
        increase(){
           this.like += 1;
        },
        sortPrice(){
            this.list.sort(function(a,b){
                return a.price - b.price
            });
        },
        sortPrice2(){
            this.list = [...this.listorigin];
        }
    },
    components: {
        discount : discountData,
        modal : modaltData,
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
.header {width: 100%; background-color: beige;}
.header a {margin-right: 30px; font-size: 20px;}
h4 {cursor: pointer;}
.black_bg {width: 100%; height: 100%; background: rgba(0, 0 ,0 ,0.5); position: fixed; padding: 20px; box-sizing: border-box;}
.white_bg {width: 100%; background: white; border-radius: 8px; padding: 20px;}
</style>
