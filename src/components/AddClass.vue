<script setup>
    import {ref} from 'vue';
    const courseName = ref("");
    const weightedCourse = ref("");
    const courseGrade = ref("");
    const emit = defineEmits(["courseSubmitEvent"]);

    const Submit = (e) => {
        if (!courseName.value || !courseGrade.value || weightedCourse.value == null) {
            alert("All fields must be filled!");
            return;
        };
        const data = {
            text: courseName.value,
            grade: parseInt(courseGrade.value),
            weightedCourse: parseInt(weightedCourse.value)
        };
        emit("courseSubmitEvent", data);
        e.target.reset();
        courseName.value = "";
        courseGrade.value = "";
        weightedCourse.value = "";
    };
</script>

<template>
    <h2>Add a Course</h2> 
    <form @submit.prevent="Submit">
        <label for="courseName">Course Name</label>
        <input type="text" id="courseName" placeholder="Enter your course..." v-model="courseName"/>
        
        <label for="weightedCourse">Is the Course AP/IB?</label>
        <input type="radio" id="true" value=1 v-model="weightedCourse" />
        <label for="true">Yes</label>

        <input type="radio" id="false" value=0 v-model="weightedCourse" />
        <label for="false">No</label>

        <label for="courseGrade">What Grade was the course?</label>
        <select v-model="courseGrade" id="courseGrade">
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
    h2 {
    margin-bottom: 1rem;
    }

    label {
        font-size:1.5rem;
        display: block;
    }

    label[for="true"], label[for="false"]{
        display: inline;
    }

    input, select{
        margin-bottom: 2rem;
    }
    input[type="text"] {
        border: 1px solid white;
        border-radius: 5px;
        display: block;
        font-size: 1.5rem;
        padding: 0.75rem;
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