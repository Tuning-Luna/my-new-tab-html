<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const logoRef = ref<HTMLDivElement | null>(null)

function goGoogle() {
  window.location.href = 'https://www.google.com'
}

onMounted(() => {
  const logo = logoRef.value
  if (!logo) return

  const onMove = (e: MouseEvent) => {
    const { left, top, width, height } = logo.getBoundingClientRect()
    const px = (e.clientX - left - width / 2) / (width / 2)
    const py = (e.clientY - top - height / 2) / (height / 2)
    logo.style.setProperty('--rotateX', `${-30 * py}deg`)
    logo.style.setProperty('--rotateY', `${30 * px}deg`)
  }

  const onLeave = () => {
    logo.style.setProperty('--rotateX', '0deg')
    logo.style.setProperty('--rotateY', '0deg')
  }

  logo.addEventListener('mousemove', onMove)
  logo.addEventListener('mouseleave', onLeave)

  onUnmounted(() => {
    logo.removeEventListener('mousemove', onMove)
    logo.removeEventListener('mouseleave', onLeave)
  })
})
</script>

<template>
  <div class="logo" ref="logoRef">
    <img class="google" src="../assets/google_logo.svg" alt="logo" @click="goGoogle" />
    <div class="avatar">
      <img src="../assets/Tuning.png" alt="" />
    </div>
  </div>
</template>

<style scoped lang="scss">
.logo {
  position: relative;
  z-index: 2;
  --rotateX: 0deg;
  --rotateY: 0deg;
  transform-style: preserve-3d;

  .google {
    width: 400px;
    height: auto;
    transition: all 0.4s ease;
    transform: rotateX(var(--rotateX)) rotateY(var(--rotateY));
    filter: drop-shadow(0 0 6px rgba(255, 255, 255, 0.4));
    animation: idle 12s ease-in-out infinite;
    transform-style: preserve-3d;
    will-change: transform;

    &:hover {
      transform: scale(1.1) rotateX(var(--rotateX)) rotateY(var(--rotateY)) translateZ(-25px);
      filter:
        drop-shadow(0 0 6px rgba(0, 255, 255, 0.7)) drop-shadow(0 0 12px rgba(0, 200, 255, 0.5)) drop-shadow(0 0 20px rgba(0, 150, 255, 0.4));
    }
  }
}

.avatar {
  position: absolute;
  bottom: -240px;
  left: 50%;
  transform: translateX(-50%);
  width: 200px;
  height: 200px;
  border-radius: 50%;
  overflow: visible;
  z-index: 3;

  img {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    border: 4px solid #00ffff;
    box-shadow: 0 0 15px rgba(0, 255, 255, 0.4);
    display: block;
    object-fit: cover;
    object-position: center;
  }

  &::after {
    content: '';
    position: absolute;
    inset: -12px;
    border-radius: 50%;
    border: 2px solid rgba(0, 255, 255, 0.5);
    animation: ripple 2s infinite linear;
    pointer-events: none;
  }
}

@keyframes idle {
  0%, 100% { transform: rotateX(6deg) rotateY(-6deg); }
  25% { transform: rotateX(-6deg) rotateY(-6deg); }
  50% { transform: rotateX(-6deg) rotateY(6deg); }
  75% { transform: rotateX(6deg) rotateY(6deg); }
}

@keyframes ripple {
  0% { inset: 0px; opacity: 1; }
  100% { inset: -40px; opacity: 0; }
}
</style>
