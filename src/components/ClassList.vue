<script setup>
    //Importing the data variable from app.vue
    import {defineProps} from "vue";
    //This variable, emit, is calculated in App.vue, then gets emitted here as "courseDeleteEvent"
    const emit = defineEmits(["courseDeleteEvent"]);
    const props = defineProps({
        courses: {
            type: Array,
            required: true
        }
    })
</script>

<template>
    <h2>📚Classes</h2>
    <ul class="list" id="list">
        <li v-for="course in courses" :key="course.id" :class="course.weighted ? 'weighted' : ''"><span class="course">{{ course.text }}</span>
            <span class="grade">{{ course.grade }}</span> 
            <button class="delete-btn" @click="emit('courseDeleteEvent', course.id);">x</button>
        </li>
    </ul>
</template>

<style scoped>

h2 {
  margin-bottom: 0;
}
.list {
  list-style-type: none;
  padding: 0;
  margin-bottom: 1rem;
}

.list li {
  background-color: white;
  border-radius: 5px;
  color: black;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  margin: 1rem 0;
}
.list li .course{
    min-width: 10rem;
}

.list li .grade{
    font-weight: bolder;
    font-size: xx-large;
}
.list li.weighted {
  background-color: #a5def2;
}

.delete-btn {
  cursor: pointer;
  background-color: red;
  border: 0;
  color: white;
  font-size: 2rem;
  line-height: 1rem;
  padding: 0.5rem;
}

.list li:hover .delete-btn {
  opacity: 1;
}
</style>