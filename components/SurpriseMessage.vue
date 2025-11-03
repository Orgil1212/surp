<template>
  <div class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 z-50">
    <div class="bg-gradient-to-br from-pink-100 to-pink-200 p-8 rounded-3xl shadow-2xl text-center relative max-w-md w-full animate-fadeIn">

      <!-- Close button -->
      <button 
        @click="$emit('close')" 
        class="absolute top-3 right-3 text-gray-500 text-3xl hover:text-pink-600 transition-transform transform hover:scale-125"
      >&times;</button>

      <!-- Header -->
      <h2 class="text-4xl font-header mb-4 text-pink-700 drop-shadow-lg animate-bounce">
        Чи миний хамгийн гайхалтай сюрприз юм шүү 🎉
      </h2>

      <!-- Body text -->
      <p class="font-body text-gray-700 mb-6 text-lg">
        Хамгийн хөөрхөн нь шүү ❤️
      </p>

      <!-- Floating Heart gif -->
      <img src="/heart.gif" alt="heart" class="mx-auto w-36 h-36 heart-float mb-6 drop-shadow-xl" />

      <!-- Button inside modal for extra interaction -->
      <button 
        @click="extraConfetti" 
        class="btn-surprise hover:scale-110 hover:rotate-2"
      >
        Илүү confetti гаргах 🎊
      </button>
    </div>
  </div>
</template>

<script setup>
import confetti from 'canvas-confetti'

// Start confetti when modal opens
const startConfetti = () => {
  confetti({
    particleCount: 180,
    spread: 140,
    origin: { y: 0.6 },
    colors: ['#FF4C4C', '#FFD700', '#FF6B6B', '#FFB6C1']
  })
}
startConfetti()

// Extra confetti button
const extraConfetti = () => {
  confetti({
    particleCount: 250,
    spread: 160,
    origin: { y: 0.6 },
    colors: ['#FF4C4C', '#FFD700', '#FF6B6B', '#FFB6C1']
  })
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Sacramento&family=Poppins:wght@400;600&display=swap');

/* Fonts */
.font-header {
  font-family: 'Sacramento', cursive;
}
.font-body {
  font-family: 'Poppins', sans-serif;
}

/* Floating heart animation */
@keyframes float {
  0% { transform: translateY(0px) rotate(0deg); }
  25% { transform: translateY(-10px) rotate(5deg); }
  50% { transform: translateY(-15px) rotate(10deg); }
  75% { transform: translateY(-10px) rotate(-5deg); }
  100% { transform: translateY(0px) rotate(0deg); }
}
.heart-float {
  animation: float 4s ease-in-out infinite;
}

/* Button inside modal */
.btn-surprise {
  background: linear-gradient(45deg, #FF6B6B, #FF4C4C);
  color: white;
  padding: 0.75rem 2rem;
  border-radius: 50px;
  font-weight: 600;
  font-family: 'Poppins', sans-serif;
  box-shadow: 0 10px 30px rgba(255, 76, 76, 0.5);
  transition: all 0.3s ease;
  cursor: pointer;
}

/* Hover effect */
.btn-surprise:hover {
  transform: scale(1.1) rotate(-2deg);
  box-shadow: 0 15px 40px rgba(255, 76, 76, 0.7);
}

/* Fade in animation for modal */
@keyframes fadeIn {
  from { opacity: 0; transform: scale(0.9); }
  to { opacity: 1; transform: scale(1); }
}
.animate-fadeIn {
  animation: fadeIn 0.35s ease-out forwards;
}

/* Bounce animation for header */
@keyframes bounce {
  0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
  40% { transform: translateY(-8px); }
  60% { transform: translateY(-4px); }
}
.animate-bounce {
  animation: bounce 2s infinite;
}
</style>
