<template>
  <div>
    <h1>swiper with axios</h1>
    <div class="container">
    	<input type='radio' id='control1' name='control' class='check' @change="cha1">
    	<input type='radio' id='control2' name='control' class='check' @change="cha2">
    	<input type='radio' id='control3' name='control' class='check' @change="cha3">
    	<input type='radio' id='control4' name='control' class='check' @change="cha4">

      <img v-for='(item,i) in songs' :src='item.pic'>

    	<div class="focus">
    		<label for='control1'></label>
    		<label for='control2'></label>
    		<label for='control3'></label>
    		<label for='control4'></label>
    	</div>
    	<div class="prev" @click='prev'><div></div></div>
    	<div class="next" @click='next'><div></div></div>
    </div>
    <div class='paper'></div>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'axiosUp',
    data() {
      return {
        songs: [],
        num: 0
      }
    },
    mounted() {
      let ptag = document.getElementsByClassName('check');

      axios.get('http://localhost:3000/banner?type=1').then(res => {
        this.songs = res.data.banners.splice(7);
        console.log(this.songs);
      });

      ptag[0].checked = 'checked';

      setInterval(() => {
      	this.num++;
      	if(this.num>ptag.length-1){
      		this.num = 0;
      	}
      	ptag[this.num].checked = 'checked'
      },4000);
    },
    methods: {
      cha1 () {
        this.num = 0
      },
      cha2 () {
        this.num = 1
      },
      cha3 () {
        this.num = 2
      },
      cha4 () {
        this.num = 3
      },
      prev () {
        let ptag = document.getElementsByClassName('check');
        this.num--;
        if(this.num < 0){
        	this.num = 3;
        }
        ptag[this.num].checked = 'checked';
      },
      next () {
        let ptag = document.getElementsByClassName('check');
        this.num++;
        if(this.num>ptag.length-1){
        	this.num = 0;
        }
        ptag[this.num].checked = 'checked';
      }
    }
  }
</script>

<style scoped>
  
  .container{
  	width: 900px;
  	height: 337.68px;
  	position: relative;
  	overflow: hidden;
  	margin: 0 auto;
  }
  img{
  	width: 900px;
  	position: absolute;
  	transition: 0.5s ease-in-out;
  }
  img:nth-of-type(1){
  	left: 0
  }
  img:nth-of-type(2){
  	left: 100%
  }
  img:nth-of-type(3){
  	left: 200%
  }
  img:nth-of-type(4){
  	left: 300%
  }
  .focus{
  	position: relative;
  	z-index: 2;
  	left: calc(50% - 30px);
  	top: 300px;
  }
  .prev, .next{
  	width: 50px;
  	text-align: center;
  	height: 100px;
  	line-height: 100px;
  	background-color: rgba(0,0,0,0.3);
  	position: absolute;
  	top: 100px;
  	z-index: 3;
  	border-radius: 25px;
  }
  .prev{
  	left: 5px;
  }
  .prev div, .next div{
  	position: absolute;
  	display: inline-block;
  	padding: 0;
  	border-width: 15px;
  	border-style: solid
  }
  .next{
  	right: 5px;
  }
  .next div{
  	border-color: transparent transparent transparent #fff;
  	top: 35px;
  	left: 20px;
    border-radius: 6px;
  }

  .prev div{
  	border-color: transparent #fff transparent transparent;
  	top: 35px;
  	left: 0px;
    border-radius: 6px;
  }

  .focus label{
  	display: inline-block;
  	width: 10px;
  	height: 10px;
  	margin: 0 4px;
  	border: 2px solid #fff;
  	border-radius: 10px;
  	box-shadow: 0 0 5px #999;
  	background-color: none;
    transition: 0.5s ease-in-out;
  }

  .check{
  	display: none;
  }

  .check:nth-of-type(1):checked~ img{
  	transform: translateX(0);
  }

  .check:nth-of-type(2):checked~ img{
  	transform: translateX(-100%);
  }

  .check:nth-of-type(3):checked~ img{
  	transform: translateX(-200%);
  }

  .check:nth-of-type(4):checked~ img{
  	transform: translateX(-300%);
  }

  .check:nth-of-type(1):checked~ .focus label:nth-of-type(1){
  	background-color: #fff;
    width: 20px
  }
  .check:nth-of-type(2):checked~ .focus label:nth-of-type(2){
  	background-color: #fff;
    width: 20px
  }
  .check:nth-of-type(3):checked~ .focus label:nth-of-type(3){
  	background-color: #fff;
    width: 20px
  }
  .check:nth-of-type(4):checked~ .focus label:nth-of-type(4){
  	background-color: #fff;
    width: 20px
  }
</style>
