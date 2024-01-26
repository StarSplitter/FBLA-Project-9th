<script setup>
    //Importing necessary materials and components from vue files and vue-toastification
    import {ref, computed, onMounted} from 'vue';
    import Header from "./components/Header.vue";
    import ClassList from "./components/ClassList.vue";
    import AddClass from "./components/AddClass.vue";
    import DisplayGPA from "./components/DisplayGPA.vue";
    import { useToast } from 'vue-toastification';
    //Sets variable for the toastification.
    const toast = useToast();
    //This variable is the array for all of the user's classes.
    const courses = ref([]);
    onMounted(() => {
        const savedData = JSON.parse(localStorage.getItem("courses"));
        if (savedData === true) {
            courses.value = savedData;
        }
    });
    const unweightedGPA = computed(() => {
        if (courses.value.length === 0){
            return 0.0;
        }
        return courses.value.reduce((a, course) => {
            return a + course.grade;
        }, 0) / courses.value.length;
    });
    const weightedGPA = computed(() => {
        if (courses.value.length === 0){
            return 0.0;
        };
        //need to fix ahhh!!!
        return (courses.value.reduce((a, course) => {
            if (course.weightedCourse === "true"){ return a + course.grade + 1};
            return a + course.grade;
        }, 0) 
        / courses.value.length);
    });
    const courseSubmitted = (courseData) => {
        courses.value.push({
            id: Math.floor(Math.random() * 100000000),
            text: courseData.text,
            grade: courseData.grade,
        });
        localStorage.setItem("courses", JSON.stringify(courses.value));
    }
    const courseDeleted = (id) => {
        courses.value = courses.value.filter((course) => 
            course.id !== id
        );
        localStorage.setItem("courses", JSON.stringify(courses.value));
        toast.success('Transaction deleted.');
    };
</script>

<template>
    <div id="container">
        <Header />
        <DisplayGPA :unweightedGPA="unweightedGPA" :weightedGPA="weightedGPA"/>
        <ClassList :courses="courses" @courseDeleteEvent="courseDeleted"/>
        <AddClass @courseSubmitEvent="courseSubmitted"/>
    </div>
</template>