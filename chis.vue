<template>
    <div>
      <h2>ساعت دیجیتالی 🕛</h2>
      <div>{{ time }}</div>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted, onUnmounted } from 'vue'
  
  // ۱. تعریف یک متغیر واکنش‌گرا (Reactive) برای زمان
  const time = ref('00:00:00')
  
  // ۲. تابعی برای به‌روزرسانی زمان
  function updateTime() {
    const now = new Date()
    const h = String(now.getHours()).padStart(2, '0')
    const m = String(now.getMinutes()).padStart(2, '0')
    const s = String(now.getSeconds()).padStart(2, '0')
    time.value = `${h}:${m}:${s}`
  }
  
  // ۳. شروع تایمر هنگام سوار شدن کامپوننت (Mount)
  let timerId = null
  onMounted(() => {
    updateTime()
    timerId = setInterval(updateTime, 1000)
  })
  
  // ۴. پاک کردن تایمر هنگام خارج شدن از DOM (Unmount)
  onUnmounted(() => {
    clearInterval(timerId)
  })
  </script>
  
  <style scoped>
  div {
    font-family: 'Courier New', monospace;
    font-size: 2rem;
    text-align: center;
    margin-top: 2rem;
  }
  </style>
  