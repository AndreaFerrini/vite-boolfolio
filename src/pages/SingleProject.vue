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
        axios.get(`${this.baseUrl}/api/projects/${this.$route.params.slug}`)
        .then((res)=>{
          if (res.data.success){
            this.project = res.data.project;
          } else {
            this.$router.push({name: 'not-found'})
          }
        });
    },

    goBack(){
        this.$router.go(-1);
    }
   }
}
</script>

<template>

  <div class="container mt-3">
    <h1 class="text-center mb-2" v-if="project">Project Singolo: {{ project.title }}</h1>
    <img class="img-fluid img-progetto" :src="`${baseUrl}/storage/${project.cover_image}`" alt="">

    <div>
        <a href="" @click.prevent="goBack" class="btn btn-info mt-3">Go Back</a>
    </div>
  </div>
</template>

<style>

li{
  list-style-type: none;
}

.img-progetto{
    width: 100%;
    height: 100%;
}

</style>