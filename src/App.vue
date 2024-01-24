<script setup>
    import {ref, computed} from 'vue';
    import Header from "./components/Header.vue";
    import ClassList from "./components/ClassList.vue";
    import AddClass from "./components/AddClass.vue";
    import DisplayGPA from "./components/DisplayGPA.vue";
    import { useToast } from 'vue-toastification';

    const toast = useToast();

    const courses = ref([]);
    const unweightedGPA = computed(() => {
        return courses.value.reduce((a, course) => {
            return a + course.grade;
        }, 0) / courses.value.length;
    });
    const weightedGPA = computed(() => {
        return courses.value.reduce((a, course) => {
            if (course.weighted){
                return a + course.grade + 1;
            } else {
                return a + course.grade;
            }
        }, 0) / courses.value.length;
    });
    const courseSubmitted = (courseData) => {
        courses.value.push({
            id: Math.floor(Math.random() * 10000000),
            text: courseData.text,
            grade: courseData.grade,
        });
        localStorage.setItem('courses', JSON.stringify(courses.value));
    }
</script>

<template>
    <div id="container">
        <Header />
        <DisplayGPA :unweightedGPA="unweightedGPA" :weightedGPA="weightedGPA"/>
        <ClassList :courses="courses"/>
        <AddClass @courseSubmitEvent="courseSubmitted"/>
    </div>
</template>