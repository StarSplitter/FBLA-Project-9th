<script setup>
  import { defineProps } from 'vue';
  
  const props = defineProps({
    unweightedGPA: {
      type: Number,
      required: true,
    },
    weightedGPA: {
      type: Number,
      required: true,
    },
  });
</script>

<template>
  <div>
  <h2>Unweighted GPA</h2>
  <p>{{ unweightedGPA }}</p>
  </div>
  <div>
  <h2>Weighted GPA</h2>
  <p>{{ weightedGPA }}</p>
  </div>
</template>
  
  