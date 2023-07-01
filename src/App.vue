<script>
import axios from "axios";

export default{
  data(){
    return{
      projects: [],
      baseUrl: "http://127.0.0.1:8000"


    }
  },
  mounted(){
    this.getProjects();

  },
  methods: {
    getProjects(){
      axios.get("{$this.baseUrl}/api/projects")
        .then( res => {
          console.log(res.data)
          this.projects = res.data.projects
        })
    }

  }
}
</script>

<template>
  <h1>Prova</h1>

  <div class="container">
    <div class="row">
      <div class="col-6" v-for="(elem,index) in projects" :key="index">
        <div class="card">
          <img class="card-img-top" :src="'${baseUrl}/storage/${elem.cover_image}'" alt="Title">
          <div class="card-body">
            <h4 class="card-title">{{elem.title}}</h4>
            <p class="card-text">{{elem.content}}</p>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<style>
</style>
