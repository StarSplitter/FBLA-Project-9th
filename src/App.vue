<script>
    import Header from "./components/Header.vue";
    import ClassList from "./components/ClassList.vue";
    import AddClass from "./components/AddClass.vue";
    import DisplayGPA from "./components/DisplayGPA.vue";

    export default{
        components: {
            Header,
            ClassList,
            AddClass,
            DisplayGPA
        }
    }
</script>

<template>
    <Header />
    <ClassList />
    <div class="search-box">
        <input type="text" placeholder="Your course here..." v-model="course" aria-label="Your course here..." aria-describedby="basic-addon2">
        <button class="btn btn-outline-secondary" type="button" @click="getCourse(course)">Button</button>
    </div>
</template>