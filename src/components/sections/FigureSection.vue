<script setup>
import SectionWrapper from '../SectionWrapper.vue'

const props = defineProps({
  id: { type: String, required: true },
  title: { type: String, required: true },
  src: { type: String, required: true },
  alt: { type: String, default: '' },
})

const rawBase = import.meta.env.BASE_URL
const base = rawBase.endsWith('/') ? rawBase : `${rawBase}/`
</script>

<template>
  <SectionWrapper :id="id" :title="title">
    <div class="figure-card">
      <img :src="`${base}${src}`" :alt="alt" class="figure-img" />
    </div>
  </SectionWrapper>
</template>

<style scoped>
.figure-card {
  background: var(--bg-card);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-lg);
  overflow: hidden;
  box-shadow: var(--shadow-card);
  padding: 16px;
}

.figure-img {
  display: block;
  width: 100%;
  height: auto;
  border-radius: var(--radius-md);
}
</style>
