<template>
  <link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&display=swap" rel="stylesheet">

  <div>
    <h2>ساعت دیجیتالی🕛</h2>
    <div>{{ time }}</div>
  </div>
</template>

<script setup>
import { onMounted, onUnmounted, ref  } from 'vue'

    let time=ref('00:00:00')
    
      function timer(){
        let now = new Date();
        let h = String(now.getHours()).padStart(2 , '0');
        let m = String(now.getMinutes()).padStart(2 , '0');
        let s = String(now.getSeconds()).padStart(2 , '0');
        time.value =` ${h}:${m}:${s}`
      }
    onMounted(()=>{
      timer()
      t = setInterval(timer,1000)
    })
    onUnmounted(()=>{
      clearInterval(t)
    })

</script>

<style lang="css" scoped>
div {
  font-family: 'Share Tech Mono', monospace;
  font-size: 3rem;
  color: lime;
  background-color: black;
  padding: 20px;
  border-radius: 10px;
  display: inline-block;
  letter-spacing: 2px;
  text-align: center;
}


</style>