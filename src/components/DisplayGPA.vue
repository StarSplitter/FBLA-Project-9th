<script setup>
  //Importing the gpa variables from app.vue 
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

  const alert = (message) => {
    return window.alert(message);
  }
</script>

<template>
  <div id="gpacontainer">
    <div>
      <p>{{ unweightedGPA.toFixed(3) }}</p>
      <h3>Unweighted GPA</h3>
      <button class="info-btn" @click="alert('Unweighted GPA is the grade average based on a 4.0 scale and does not consider course difficulty.');">?</button>
    </div>
    <div>
      <p>{{ weightedGPA.toFixed(3) }}</p>
      <h3>Weighted GPA</h3>
      <button class="info-btn" @click="alert('Weighted GPA is the grade average based on a 5.0 scale and does consider course difficulty.');">?</button>
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
    font-size: 1.5rem;
  }
  p{
    font-size: 2rem;
    font-weight: bolder;
  }
  .info-btn{
    cursor: pointer;
    margin-top: -1rem;
    font-size: 1.5rem;
    background-color: lightblue;
    min-width: 1.5rem;
  }
</style>
  