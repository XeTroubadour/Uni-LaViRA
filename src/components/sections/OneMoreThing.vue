<script setup>
import SectionWrapper from '../SectionWrapper.vue'

const rawBase = import.meta.env.BASE_URL
const base = rawBase.endsWith('/') ? rawBase : `${rawBase}/`
const videoSrc = `${base}video_compressed/02.mp4`
</script>

<template>
  <SectionWrapper id="onemorething" title="One More Thing">
    <video
      :src="videoSrc"
      controls
      preload="metadata"
      playsinline
      class="omt-video"
    ></video>
  </SectionWrapper>
</template>

<style scoped>
.omt-video {
  display: block;
  width: 100%;
  height: auto;
  border-radius: var(--radius-md);
  border: 1px solid var(--border-subtle);
  background: var(--bg-card);
}
</style>
