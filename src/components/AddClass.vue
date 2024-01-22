<script setup>
    import {ref} from 'vue';
    const courseName = ref('');
    const weightedCourse = ref(false)
    const courseGrade = ref('')
</script>

<template>
    <h2>Add a Course</h2> 
    <form>
        <label for="courseName">Course Name</label>
        <input type="text" id="courseName" placeholder="Enter your course..." v-model="courseName"/>
        
        <input type="radio" id="true" value=true v-model="weightedCourse" />
        <label for="true">Yes</label>

        <input type="radio" id="false" value=false v-model="weightedCourse" />
        <label for="false">No</label>

        <select v-model="courseGrade">
            <option disabled value="">Please select one</option>
            <option>0</option>
            <option>1</option>
            <option>2</option>
            <option>3</option>
            <option>4</option>
        </select>

        <button>Submit Course</button>
    </form>
</template>

<style scoped>
    label {
        font-size:1.5rem;
        margin: 10px 0;
    }

    input[type='text'],
    input[type='number'] {
        border: 1px solid #dedede;
        border-radius: 2px;
        display: block;
        font-size: 16px;
        padding: 10px;
        width: 100%;
    }

    button {
        cursor: pointer;
        background-color: lightblue;
        color:white;
        border: 1px solid black;
        border-radius: 10px;
        font-size: 2rem;
        margin-bottom: 1rem;
        padding: 2rem;
        width: 100%;
    }
    button:hover{
        color:blue;
    }
</style>