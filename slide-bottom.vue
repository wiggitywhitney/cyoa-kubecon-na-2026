<!-- Small voting QR code in the bottom-left corner of every slide. -->
<!-- A slide opts out with `qr: false` in its frontmatter. -->
<script setup lang="ts">
import { computed } from 'vue'
import { useSlideContext } from '@slidev/client'

const { $frontmatter } = useSlideContext()
const show = computed(() => $frontmatter?.qr !== false)
// BASE_URL keeps the image path right when the deck is built under a subpath (GitHub Pages).
const qrSrc = `${import.meta.env.BASE_URL}vote-qr.png`
</script>

<template>
  <img v-if="show" :src="qrSrc" alt="QR code to vote" class="corner-qr" />
</template>

<style scoped>
.corner-qr {
  position: absolute;
  left: 16px;
  bottom: 16px;
  width: 96px;
  height: 96px;
  z-index: 10;
}
</style>
