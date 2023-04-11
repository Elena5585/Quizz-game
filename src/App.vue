<template>
  <div class="quizz">
      <div v-if="count === 0" class="quizz__content">
          <img src="./assets/quiz.svg" alt="">
          <input type="text" v-model="username" class="username">
          <button class="btn__next" @click="start()">START</button>          
      </div>
      <div v-if="count === 1" class="quizz__content">
          <First :first="first" :user="user" @score-plus="countScore()"></First>
          <button class="btn__next" @click="counter()">NEXT</button>
      </div>
      <div v-if="count === 2" class="quizz__content">
          <Second :second="second" :user="user" @score-plus="countScore()"></Second>
          <button class="btn__next" @click="counter()">NEXT</button>
      </div>
      <div v-if="count === 3" class="quizz__content">
          <Third :third="third" :user="user" @score-plus="countScore()"></Third>
          <button class="btn__next" @click="counter()">NEXT</button>
      </div>
      <div v-if="count === 4" class="quizz__content">
          <Fourth :fourth="fourth" :user="user" @score-plus="countScore()"></Fourth>
          <button class="btn__next" @click="counter()">NEXT</button>
      </div>
      <div v-if="count === 5" class="quizz__content">
          <Fifth :fifth="fifth" :user="user" @score-plus="countScore()"></Fifth>
          <button class="btn__next" @click="counter()">NEXT</button>
      </div>
      <div v-if="count > 5" class="quizz__content">
          <Last :score="score" :user="user"></Last>
          <button class="btn__next" @click="finish()">FINISH</button>
      </div>
  </div>
  
</template>

<script>

import First from './components/First.vue';
import Second from './components/Second.vue';
import Third from './components/Third.vue';
import Fourth from './components/Fourth.vue';
import Fifth from './components/Fifth.vue';
import Last from './components/Last.vue';

export default {
  name: 'App',
  components: {      
      First,
      Second,
      Third,
      Fourth,
      Fifth,
      Last,
  },
  data(){
    return{
      username: '',
      user: '',
      count: 0,
      score: 0,
      first: {question: 'What is the capital of the United Kingdom?', A: 'New York', B: 'London', C: 'Chelsi', D: 'Paris', answer: 'B'},
      second: {question: 'What is the capital of Brazil?', A: 'Rio de Janeiro', B: 'Mexico', C: 'Brasilia', D: 'Monaco', answer: 'C'},
      third: {question: 'What is the capital of Italy?', A: 'Rome', B: 'Milan', C: 'Venice', D: 'Florencia', answer: 'A'},
      fourth: {question: 'What is the capital of the Russian Federation?', A: 'New York', B: 'Moscow', C: 'Saint Petersburg', D: 'Sochi', answer: 'B'},
      fifth: {question: 'What is the capital of the United States of America?', A: 'New York', B: 'Washington', C: 'Los Angeles', D: 'Paris', answer: 'B'},
    }
  },  
  methods:{
    start(){
      this.count = 0;
      localStorage.clear();
      localStorage.setItem('username', this.username);   
      this.user = localStorage.getItem('username');   
      this.count++;
      console.log(localStorage.username);
      console.log(this.count);
    },
    counter(){
      this.count++;      
    }, 
    finish(){
      this.count = 0;
      localStorage.clear();
      this.username = '';
      this.score = 0;
    } ,
    countScore(){
      this.score += 1;
      console.log(this.score);
    }  
  }
}
</script>

<style>
html, body{width: 100%;  margin: 0; padding: 0; box-sizing: border-box; overflow: hidden;}
#app {width: 100%; height: 100vh; background-image: url(./assets/background.svg); background-repeat: no-repeat; background-size: cover;
margin: 0 auto; padding: 20px;}
.quizz{display: flex; flex-direction: column; align-items: center; justify-content: start; height: 100%; width: 50%; margin: 0 auto;}
.quizz__content{width: 100%; height: 100%; display: flex; flex-direction: column; align-items: center; justify-content: start; row-gap: 10px;
font-size: 1.6rem; font-weight: 500; }
img{z-index: 0; height: auto;margin-top: 10%; border: none}
.btn__next{width: 100%; height: 60px; background-color: rgb(222, 68, 68); border: none; outline: none; color: rgb(246, 242, 242); 
text-transform: uppercase; font-size: 1.6rem; font-weight: 600; box-shadow: 2px 2px 2px 2px grey; border-radius: 10px; letter-spacing: 1px; margin-top: 0;}
.username{border: none; outline: none; border-radius: 10px; box-shadow: 5px 5px 0 0px grey; font-size: 1.7rem; font-weight: 600; left: 1px;
text-align: center; width: 95%; padding: 10px 15px; margin-block: 15px;}
</style>
