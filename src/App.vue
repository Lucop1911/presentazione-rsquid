<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import SlideHero from './components/SlideHero.vue'
import SlideTech from './components/SlideTech.vue'
import SlideArch from './components/SlideArch.vue'
import SlideConnections from './components/SlideConnections.vue'
import SlideQuery from './components/SlideQuery.vue'
import SlideCredits from './components/SlideCredits.vue'

const slides = [SlideHero, SlideTech, SlideArch, SlideConnections, SlideQuery, SlideCredits]
const activeIndex = ref(0)
const totalSlides = slides.length

function goTo(i) {
  const idx = Math.max(0, Math.min(i, totalSlides - 1))
  document.querySelectorAll('.slide')[idx]?.scrollIntoView({ behavior: 'smooth' })
}

function onKeydown(e) {
  if (e.key === 'ArrowDown') goTo(activeIndex.value + 1)
  if (e.key === 'ArrowUp') goTo(activeIndex.value - 1)
}

let observer
onMounted(() => {
  observer = new IntersectionObserver(
    (entries) => {
      for (const e of entries) {
        if (e.isIntersecting) {
          activeIndex.value = Number(e.target.dataset.index)
        }
      }
    },
    { threshold: 0.45 }
  )
  document.querySelectorAll('.slide').forEach((el, i) => {
    el.dataset.index = i
    observer.observe(el)
  })
  window.addEventListener('keydown', onKeydown)
})

onUnmounted(() => {
  observer?.disconnect()
  window.removeEventListener('keydown', onKeydown)
})
</script>

<template>
  <div class="presentation">
    <nav class="nav-dots">
      <button
        v-for="(_, i) in slides"
        :key="i"
        class="nav-dot"
        :class="{ active: activeIndex === i }"
        @click="goTo(i)"
        :aria-label="'Vai alla slide ' + (i + 1)"
      />
    </nav>

    <div class="nav-hint">&uarr;&darr;  usa i puntini a destra</div>

    <SlideHero />
    <SlideTech />
    <SlideArch />
    <SlideConnections />
    <SlideQuery />
    <SlideCredits />
  </div>
</template>
