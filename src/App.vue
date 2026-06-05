<script setup lang="ts">
import Logo3D from './components/Logo3D.vue'
import TypeWriter from './components/TypeWriter.vue'
</script>

<template>
  <div class="main">
    <Logo3D />
    <TypeWriter />
  </div>
</template>

<style scoped lang="scss">
.main {
  position: relative;
  width: 100vw;
  height: 100vh;
  background: url('./assets/earch.jpg') no-repeat center center / cover;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  padding-top: 20vh;
  perspective: 1000px;

  &::before {
    content: '';
    position: absolute;
    inset: 0;
    background:
      radial-gradient(circle at 30% 30%, rgba(0, 80, 255, 0.25), transparent 50%),
      radial-gradient(circle at 70% 70%, rgba(255, 0, 150, 0.2), transparent 50%);
    animation: nebulaMove 20s linear infinite alternate;
    z-index: 0;
  }

  &::after {
    content: '';
    position: absolute;
    inset: 0;
    background:
      radial-gradient(4px 4px at 5% 10%, rgba(220, 235, 255, 1), transparent),
      radial-gradient(3px 3px at 15% 35%, rgba(255, 240, 250, 0.98), transparent),
      radial-gradient(4.5px 4.5px at 25% 60%, rgba(210, 230, 255, 1), transparent),
      radial-gradient(3px 3px at 35% 20%, rgba(245, 230, 255, 0.98), transparent),
      radial-gradient(2.5px 2.5px at 45% 50%, rgba(235, 245, 255, 0.95), transparent),
      radial-gradient(4px 4px at 55% 80%, rgba(255, 245, 250, 1), transparent),
      radial-gradient(3px 3px at 65% 30%, rgba(220, 235, 255, 1), transparent),
      radial-gradient(2.5px 2.5px at 75% 70%, rgba(240, 250, 255, 0.95), transparent),
      radial-gradient(4px 4px at 85% 40%, rgba(255, 240, 250, 1), transparent),
      radial-gradient(2.5px 2.5px at 95% 90%, rgba(230, 240, 255, 0.95), transparent),
      radial-gradient(3.2px 3.2px at 10% 50%, rgba(210, 230, 255, 1), transparent),
      radial-gradient(4px 4px at 20% 80%, rgba(230, 245, 255, 1), transparent),
      radial-gradient(2.8px 2.8px at 30% 15%, rgba(255, 235, 250, 0.98), transparent),
      radial-gradient(3.5px 3.5px at 40% 65%, rgba(210, 230, 255, 1), transparent),
      radial-gradient(4.3px 4.3px at 50% 25%, rgba(220, 235, 255, 1), transparent),
      radial-gradient(2.5px 2.5px at 60% 75%, rgba(255, 240, 250, 0.95), transparent),
      radial-gradient(4px 4px at 70% 10%, rgba(210, 230, 255, 1), transparent),
      radial-gradient(3px 3px at 80% 55%, rgba(230, 245, 255, 1), transparent),
      radial-gradient(4.5px 4.5px at 90% 30%, rgba(255, 245, 250, 1), transparent),
      radial-gradient(3px 3px at 0% 70%, rgba(220, 235, 255, 1), transparent),
      radial-gradient(2.8px 2.8px at 12% 90%, rgba(235, 230, 255, 0.95), transparent),
      radial-gradient(3.5px 3.5px at 22% 5%, rgba(255, 235, 245, 0.98), transparent),
      radial-gradient(4px 4px at 32% 45%, rgba(210, 230, 255, 1), transparent),
      radial-gradient(2.5px 2.5px at 42% 85%, rgba(220, 235, 255, 1), transparent),
      radial-gradient(4.3px 4.3px at 52% 20%, rgba(255, 240, 250, 1), transparent),
      radial-gradient(3px 3px at 62% 60%, rgba(230, 245, 255, 1), transparent),
      radial-gradient(4px 4px at 72% 95%, rgba(255, 245, 250, 1), transparent),
      radial-gradient(3.5px 3.5px at 82% 35%, rgba(220, 235, 255, 1), transparent),
      radial-gradient(4.5px 4.5px at 92% 75%, rgba(235, 245, 255, 1), transparent);
    background-repeat: no-repeat;
    filter: brightness(1.8) blur(0.3px);
    animation: starsMove 25s linear infinite;
    z-index: 0;
  }
}

@keyframes nebulaMove {
  from { background-position: 0% 0%, 100% 100%; }
  to { background-position: 100% 100%, 0% 0%; }
}

@keyframes starsMove {
  from { background-position: 0 0, 0 0, 0 0; }
  to { background-position: 1000px 600px, -800px 600px, 600px -400px; }
}
</style>
