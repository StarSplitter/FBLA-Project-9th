<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>
  <h1>GPA Calculator</h1>
  <p>Created by Tianluo Zhu from FBLA, Palisade High School Chapter</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
