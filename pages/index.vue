<template>
  <main class="bg-main">
    <h1 class="font-header">Сюрприз! 💖</h1>
    <p class="font-body">
      Нууц мессежээ нээхийн тулд товчийг дарна уу
    </p>

    <!-- Button section -->
    <div class="btn-container">
      <button class="btn-surprise animate-slideUp" @click="openSurprise">
        Нээх
      </button>
    </div>

    <SurpriseMessage v-if="showMessage" @close="showMessage = false" />

    <!-- Floating Heart -->
    <img src="/heart.gif" class="heart-float" alt="heart" />

    <!-- Шүлгийн секц -->
    <ShulegSection />
  </main>
</template>

<script setup>
import { ref } from 'vue'
import SurpriseMessage from '~/components/SurpriseMessage.vue'
import ShulegSection from '~/components/shuleg.vue'
import confetti from 'canvas-confetti'

const showMessage = ref(false)

const openSurprise = () => {
  showMessage.value = true
  confetti({
    particleCount: 200,
    spread: 120,
    origin: { y: 0.6 },
    colors: ['#FF4C4C', '#FFD700', '#FF6B6B', '#FFB6C1']
  })
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Sacramento&family=Poppins:wght@400;600&display=swap');

/* Background */
.bg-main {
  background: linear-gradient(135deg, #FFDDE1 0%, #FFF0F5 100%);
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
}

.font-header {
  font-family: 'Sacramento', cursive;
  font-size: 4rem;
  color: #FF4C4C;
  text-align: center;
}

.font-body {
  font-family: 'Poppins', sans-serif;
  font-size: 1.25rem;
  color: #333;
  text-align: center;
  margin-bottom: 2rem;
}

/* Button */
.btn-container {
  display: flex;
  justify-content: center;
  width: 100%;
  margin-bottom: 3rem;
}

.btn-surprise {
  background: linear-gradient(45deg, #FF6B6B, #FF4C4C);
  color: white;
  padding: 1rem 2.5rem;
  border-radius: 50px;
  font-weight: 600;
  cursor: pointer;
}

.btn-surprise:hover {
  transform: scale(1.1) rotate(-2deg);
  box-shadow: 0 12px 30px rgba(255, 76, 76, 0.6);
}

/* Floating Heart */
@keyframes float {
  0% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-15px) rotate(10deg); }
  100% { transform: translateY(0px) rotate(-5deg); }
}
.heart-float {
  animation: float 3s ease-in-out infinite;
  width: 100px;
  height: 100px;
  margin: 2rem auto;
}
</style>
