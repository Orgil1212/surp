<template>
  <section class="py-20 px-6 bg-pink-50 text-center relative overflow-hidden">
    <!-- Floating hearts -->
    <div class="absolute top-0 left-0 w-full h-full pointer-events-none">
      <span v-for="n in 10" :key="n" class="heart absolute text-pink-400 text-2xl">❤️</span>
    </div>

    <h3 class="text-3xl font-header text-pink-600 mb-12 animate-fadeIn">Миний зүрхний шүлэг</h3>
    
    <div class="max-w-xl mx-auto space-y-8">
      <p class="font-body text-gray-700 text-lg animate-slideUp">
        Чамайг анх харсан мөчөөс эхлэн,<br>
        Миний сэтгэл чам руу нисэн очсон.
      </p>
      <p class="font-body text-gray-700 text-lg animate-slideUp delay-200">
        Чиний инээмсэглэл нарны туяа шиг,<br>
        Миний өдөр бүрийг гэрэлтүүлдэг.
      </p>
      <p class="font-body text-gray-700 text-lg animate-slideUp delay-400">
        Чамтай өнгөрүүлсэн мөчүүд бол гайхалтай аялал,<br>
        Сэтгэлд минь үүрд хадгалагдсан дурсамж.
      </p>
      <p class="font-body text-gray-700 text-lg animate-slideUp delay-600">
        Чамд би хайртайгаа хэлэх үедээ,<br>
        Зүрх минь баяр хөөрөөр дүүрнэ.
      </p>
    </div>
  </section>
</template>

<script setup>
import { onMounted } from 'vue'
import confetti from 'canvas-confetti'

onMounted(() => {
  // Light confetti effect when page loads
  confetti({
    particleCount: 100,
    spread: 80,
    origin: { y: 0.6 },
    colors: ['#FF4C4C', '#FFB6C1', '#FFD700']
  })
})
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Sacramento&family=Poppins:wght@400;600&display=swap');

.font-header {
  font-family: 'Sacramento', cursive;
}
.font-body {
  font-family: 'Poppins', sans-serif;
  line-height: 1.8;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
.animate-fadeIn {
  animation: fadeIn 1s ease-out forwards;
}

@keyframes slideUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}
.animate-slideUp {
  animation: slideUp 0.8s ease-out forwards;
}
.delay-200 { animation-delay: 0.2s; }
.delay-400 { animation-delay: 0.4s; }
.delay-600 { animation-delay: 0.6s; }
</style>