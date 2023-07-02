<script>
import axios from "axios";

export default{
    name: "SingleProject",
    data() {
        return{
        baseUrl: "http://127.0.0.1:8000",
        project: null
        // currentPage: 1,
        // lastPage: null


        }
    },
  mounted(){
    console.log( this.$route );
    this.getSingleProject();

  },
  methods: {

    getSingleProject(){
        axios.get("${this.baseUrl}/api/projects/${this.$route.params.slug}")
            .then((response) => {
                this.project = response.data.project;
        }), error => {
            if( error.response.status === 404) {
                this.$router.push( {name: "not-found"})
            } else {
            
            }
        }
    }
   }
}
</script>

<template>

  <div class="container mt-3">
    <h1 class="text-center" v-if="project">Project Singolo: {{ project.title }}</h1>
    <p>{{ project.content }}</p>
    <div>
        <h2>Types:</h2>
        <ul>
            <li v-for="(elem,index) in project.types" :key="index">
                {{ elem.name }}
            </li>
        </ul>
    </div>

  </div>
</template>

<style>


li{
  list-style-type: none;
}

</style>