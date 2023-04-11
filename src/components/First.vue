<template>
      <div class="user">{{ user }}</div>
      <div class="question"><p>QUESTION 1:</p> <p>{{ first.question }}</p></div>
      <div class="option a" @click="checkAnswer($event)">A:  {{first.A }}</div>
      <div class="option b" @click="checkAnswer($event)">B:  {{first.B }}</div>
      <div class="option c" @click="checkAnswer($event)">C:  {{first.C }}</div>
      <div class="option d" @click="checkAnswer($event)">D:  {{first.D }}</div>
      <div class="answer"></div>
</template>

<script>
      export default {
            name: 'First',
            props:{
                  first:{
                        type: Object,
                        default: {},
                        required: true,
                  },
                  user:{
                        type: String,                        
                  },
                  score:{
                        type: Number,                        
                  },
            },
            data(){
                  return{
                        click: 0,
                  }
            },
            methods: {
                  
                  checkAnswer($event){
                        if(this.click === 0){ 
                              if($event.target.textContent.startsWith(this.first.answer)){
                                    $event.target.style.backgroundColor = 'green';
                                    document.querySelector('.answer').textContent = 'CORRECT...';
                                    document.querySelector('.answer').style.color = 'green';                                    
                                    this.click += 1;
                                    this.$emit('score-plus');
                              }else {
                                    $event.target.style.backgroundColor = 'red';
                                    document.querySelector('.answer').textContent = 'WRONG...';
                                    document.querySelector('.answer').style.color = 'red';
                                    this.click += 1;
                              } 
                        }                   
                        
                        
                        
                  }
            }
      }
</script>

<style scoped>
      .question{width: 100%; height: auto; background-color: rgb(93, 155, 164, 0.7); border-radius: 10px; color: black; padding: 10px;
      font-size: 1.8rem; font-weight: 600; display: flex; align-items: center; justify-content: center;flex-direction: column; row-gap: 15px; text-align: center;}
      p{margin: 0;}
      p:last-of-type{font-weight: 500;}
      div[class^=option]{width: 100%; height: 40px; background-color: rgb(93, 155, 164, 0.7); border-radius: 10px; color: black; padding: 10px;
      font-size: 1.8rem; font-weight: 500; text-transform: uppercase; display: flex; align-items: center; justify-content: center;}
      .answer{text-transform: uppercase;font-weight: 700; font-size: 1.6rem; height: 50px; margin: 0;}
      .user{text-transform: uppercase; color: rgba(18, 51, 56, 0.7); font-weight: 700; font-size: 2.2rem;margin-bottom: 10px;}
</style>