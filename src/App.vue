
<template>
    <div class="jumbotron text-center">
          <h1>GPA Calculator</h1>
          <p>Created by Tianluo Zhu from FBLA, Palisade High School Chapter</p>
      </div>
      <div class="search-box">
          <input type="text" placeholder="Your course here..." v-model="course" aria-label="Your course here..." aria-describedby="basic-addon2">
          <button class="btn btn-outline-secondary" type="button" @click="getCourse(course)">Button</button>
      </div>
      <p>{{ courses }}</p>
</template>

<script>
    export default {
        data(){
            return{
                name: 'App',
                courseName: '',
                courses: []
            }
        },
        methods: {
            async getCourse(course){
                const response = await fetch(`classes.json`);
                const data = await response.json();
                this.courseName = data.find(x => x === course).name;
            }
            
        },
        mounted(){
            fetch(`http://localhost:3000/math`)
                .then(res => res.json())
                .then(data => this.courses = data)
                .catch(err => console.log(err.message));
        }
    }
</script>