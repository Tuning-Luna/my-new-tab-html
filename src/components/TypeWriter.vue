<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const props = withDefaults(defineProps<{
  text?: string
  speed?: number
}>(), {
  text: 'Always Learning, Always building.',
  speed: 130,
})

const typingRef = ref<HTMLDivElement | null>(null)
let intervalId: ReturnType<typeof setInterval> | null = null
let timeoutId: ReturnType<typeof setTimeout> | null = null

function typeWriter(el: HTMLElement) {
  let index = 0
  let pausing = false

  intervalId = setInterval(() => {
    if (pausing) return
    el.textContent = props.text.slice(0, index++)
    if (index > props.text.length) {
      pausing = true
      timeoutId = setTimeout(() => { index = 0; pausing = false }, 2000)
    }
  }, props.speed)
}

onMounted(() => {
  if (typingRef.value) typeWriter(typingRef.value)
})

onUnmounted(() => {
  if (intervalId !== null) clearInterval(intervalId)
  if (timeoutId !== null) clearTimeout(timeoutId)
})
</script>

<template>
  <div class="typing" ref="typingRef"></div>
</template>

<style scoped lang="scss">
.typing {
  position: absolute;
  bottom: 12vh;
  left: 50%;
  transform: translateX(-50%);
  font-size: 2.8rem;
  color: #1f9797;
  font-family: monospace;
  white-space: nowrap;
  z-index: 2;
}
</style>
