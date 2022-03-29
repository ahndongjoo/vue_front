<template>
    <div class="black_bg" v-if="모달창 == false">
        <div class="white_bg">
            <h4>상세</h4>
            <h3>상세</h3>
            <button @click="모달창 = true">닫기</button>
        </div>

    </div>
    <div class="header">
        <a v-for="(a ,i) in menus" :key="i">asds</a>
    </div>
    <ul>
        <li v-for="listD in list" :key="listD">
            <img :src="listD.image">
            <p>{{listD.title}}</p>
            <p>{{listD.price}}</p>
            <span>{{listD.content}}</span>
        </li>
    </ul>
</template>

<script>
import listData from './assets/list.js'

export default {
    name: 'App',
    data(){
        return {
            list : listData,
            모달창 : true,
            menus : ['home' , 'product' , 'about'],
            product : listData,
            price : ['60' , '70', '80'],
            like : [0 , 0 , 0]
        }
    },
    methods : {
        increase(){
           this.like += 1;
           console.log(this.like);
        }
    },
    components: {
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
