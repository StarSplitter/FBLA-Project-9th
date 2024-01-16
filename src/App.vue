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
</script>

<template>
    <Header />
    <div id="container">
        <DisplayGPA :unweightedGPA="unweightedGPA"/>
        <ClassList :courses="courses"/>
        <div class="search-box">
            <input type="text" placeholder="Your course here..." v-model="course" aria-label="Your course here..." aria-describedby="basic-addon2">
            <button class="btn btn-outline-secondary" type="button" @click="getCourse(course)">Button</button>
        </div>
    </div>
</template>