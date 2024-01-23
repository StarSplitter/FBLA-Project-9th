<script setup>
    import {ref, computed} from 'vue';
    import Header from "./components/Header.vue";
    import ClassList from "./components/ClassList.vue";
    import AddClass from "./components/AddClass.vue";
    import DisplayGPA from "./components/DisplayGPA.vue";

    const courses = ref([
        {id: 1, text: "Algebra 2", weighted: false, grade: 4},
        {id: 2, text: "Honors 9th Comp", weighted: false, grade: 4},
        {id: 3, text: "AP Human Geography", weighted: true, grade: 4},
        {id: 4, text: "Honors Biology", weighted: false, grade: 3},
        {id: 5, text: "Honors Spanish I", weighted: false, grade: 3}
    ]);
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
</script>

<template>
    <div id="container">
        <Header />
        <DisplayGPA :unweightedGPA="unweightedGPA" :weightedGPA="weightedGPA"/>
        <ClassList :courses="courses"/>
        <AddClass />
    </div>
</template>