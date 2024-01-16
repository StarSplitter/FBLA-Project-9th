<script setup>
    import {defineProps} from 'vue';

    const props = defineProps({
        courses: {
            type: Array,
            required: true
        }
    })
</script>

<template>
    <h3>Classes</h3>
    <ul class="list" id="list">
        <li v-for="course in courses" :key="course.id" :class="course.weighted ? 'weighted' : ''">{{ course.text }}
            <span>{{ course.grade }}</span> 
            <button class="delete-btn">x</button>
        </li>
    </ul>
</template>