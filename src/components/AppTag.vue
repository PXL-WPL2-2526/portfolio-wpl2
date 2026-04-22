<script setup>
import { onMounted, onUnmounted, useTemplateRef, ref } from 'vue'

const tagEl = useTemplateRef('tag')
const visible = ref(true)

let observer

function fitText() {
  const el = tagEl.value
  if (!el) return

  el.style.fontSize = ''
  el.style.whiteSpace = 'nowrap'
  el.style.display = 'inline-block'

  const parentWidth = el.parentElement.offsetWidth
  const textWidth = el.scrollWidth
  const scale = parentWidth / textWidth

  el.style.fontSize = parseFloat(getComputedStyle(el).fontSize) * scale + 'px'
  el.style.display = ''
}

onMounted(() => {
  fitText()
  window.addEventListener('resize', fitText)

  const footer = document.querySelector('#footer')
  observer = new IntersectionObserver(([entry]) => {
    visible.value = !entry.isIntersecting
  })
  observer.observe(footer)
})

onUnmounted(() => {
  observer.disconnect()
  window.removeEventListener('resize', fitText)
})
</script>

<template>
  <p :class="['tag', { hidden: !visible }]" ref="tag">GIEL BOOGAERTS STUDIO</p>
</template>

<style scoped>
.tag {
  width: 100%;
  position: fixed;
  top: 50%;
  padding: 0 1rem;
  text-align-last: justify;
  font: var(--header-3);
  color: var(--dark-color);
  mix-blend-mode: screen;
  z-index: 100;
  transition: opacity 0.4s ease;
  pointer-events: none;
}

.tag.hidden {
  opacity: 0;
}
</style>
