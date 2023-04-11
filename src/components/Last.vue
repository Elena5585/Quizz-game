<template>
      <div class="user">{{ user }}</div>
      <div class="score"> YOUR SCORE : {{ score }} / 5</div>
</template>

<script>
      export default {
            name: 'Last',
            props:{
                  score:{
                        type: Number,                        
                  },
                  user:{
                        type: String,                        
                  }
            },
      }
</script>

<style scoped>
      .score{font-size: 2rem; font-weight: 700; letter-spacing: 1px; color: black; margin-top: 10%;margin-bottom: 10px;}
      .user{text-transform: uppercase; color: rgba(18, 51, 56, 0.7); font-weight: 700; font-size: 2.2rem;}
</style>