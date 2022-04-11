<template>
        <div class="black_bg" v-if="모달창 == true">
        <div class="white_bg">
            <img :src="list[state].image" style="width=100%">
            <h4>{{list[state].title}}</h4>
            <h3>{{list[state].content}}</h3>
            <h3>{{list[state].price}}원</h3>
            <button @click="모달창 = false">닫기</button>
        </div>
    </div>
</template>
<script>
export default {
    name : 'modal-div',
    props : {
        list : Array,
        modalWindow : Number,
    }
}
</script>
<style>
.black_bg {width: 100%; height: 100%; background: rgba(0, 0 ,0 ,0.5); position: fixed; padding: 20px; box-sizing: border-box;}
.white_bg {width: 100%; background: white; border-radius: 8px; padding: 20px;}
</style>
