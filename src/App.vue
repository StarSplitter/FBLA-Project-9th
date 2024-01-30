<script setup>
    //Importing necessary materials and components from vue files and vue-toastification
    import {ref, computed, onMounted} from 'vue';
    import Header from "./components/Header.vue";
    import ClassList from "./components/ClassList.vue";
    import AddClass from "./components/AddClass.vue";
    import DisplayGPA from "./components/DisplayGPA.vue";
    //This variable is the array for all of the user's classes.
    const courses = ref([]);
    //When the Website is loaded, ASAP-ly check if there are any saved data in local storage
    //If there is, set the current data to the saved data
    //the onMounted function happens right after website is loaded
    onMounted(() => {
        const savedData = JSON.parse(localStorage.getItem("courses"));
        if (savedData) {
            courses.value = savedData;
        }
    });
    //This function uses the computed property to compute the unweighted GPA
    const unweightedGPA = computed(() => {
        //If there are no courses, return GPA as 0.0
        if (courses.value.length === 0){
            return 0.0;
        }
        //Calculate the sum of all grades in courses list via reduce method, then divide by number of courses (courses.value.length)
        return courses.value.reduce((a, course) => {
            return a + course.grade;
        }, 0) / courses.value.length;
    });
    //This function uses the computed property to compute the weighted GPA
    const weightedGPA = computed(() => {
        //If there are no courses, return GPA as 0.0
        if (courses.value.length === 0){
            return 0.0;
        }
        //In order to calculated weighted GPA, find sum of all grades via reduce method
        //Then add the extra grades from AP/IB courses
        //Lastly divide by the number of courses
        return ((courses.value.reduce((a, course) => {
            return a + course.grade;
        }, 0) + (courses.value.filter((course) => course.weightedCourse == 1)).length)) / courses.value.length;
    });
    //This function takes the CourseData from the Form Component
    const courseSubmitted = (courseData) => {
        //Pushes the new object into the courses data array and sets its values based on the form
        courses.value.push({
            id: Math.floor(Math.random() * 100000000),
            text: courseData.text,
            grade: courseData.grade,
            weightedCourse: courseData.weightedCourse
        });
        //Sets the data in localStorage
        localStorage.setItem("courses", JSON.stringify(courses.value));
    }
    const courseDeleted = (id) => {
        courses.value = courses.value.filter((course) => 
            course.id !== id
        );
        localStorage.setItem("courses", JSON.stringify(courses.value));
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