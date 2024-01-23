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
  <div id="gpacontainer">
    <div>
      <p>{{ unweightedGPA }}</p>
      <h3>Unweighted GPA</h3>
    </div>
    <div>
      <p>{{ weightedGPA }}</p>
      <h3>Weighted GPA</h3>
    </div>
  </div>
</template>
  
<style scoped>
  #gpacontainer{
    display: flex;
    justify-content: space-around;
    align-items: center;
    background-color: #f7f7f7;
    border-radius: 10px;
    margin-bottom: 1rem;
  }
  
  #gpacontainer div{
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 1rem;
  }
  h3{
    margin-top: 0;
  }
  
</style>
  