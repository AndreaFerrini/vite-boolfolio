<script>
import axios from "axios";

export default{
  data() {
    return{
      projects: [],
      baseUrl: "http://127.0.0.1:8000",
      currentPage: 1,
      lastPage: null


    }
  },
  mounted(){
    this.getProjects(1);

  },
  methods: {
    getProjects(projectApiPage){

      axios.get("${this.baseUrl}/api/projects", {
        params: {
          page: projectApiPage
        }
      }).then( res => {
        
          this.projects = res.data.projects.data
          this.currentPage = res.data.projects.current_page
          this.lastPage = res.data.projects.last_page
        })
    }

  }
}
</script>

<template>

  <div class="container">
    <h1 class="text-center">Ecco i miei progetti</h1>
    <div class="row">
      <div class="col-6" v-for="(elem,index) in projects" :key="index">
        <div class="card">
          <img class="card-img-top" :src="'${baseUrl}/storage/${elem.cover_image}'" alt="Title">
          <div class="card-body">
            <h4 class="card-title">{{elem.title}}</h4>
            <p class="card-text">{{elem.content}}</p>


            <div>
              <h5>Types</h5>
              <span>{{ elem.types.name }}</span>
            </div>
            <div>
              <h5>Technologies</h5>
              <ul>
                <li class="" v-for="(elem,index) in elem.technologies" :key="index">{{ elem.name }}</li>
              </ul>
            </div>
          </div>
        </div>
      </div>


      <!-- paginazione -->
      <nav aria-label="Page navigation">
        <ul class="pagination">
          <li class="page-item">
            <a class="page-link" @click.prevent="getProjects(currentPage - 1)" href="#" aria-label="Previous">
              <span aria-hidden="true">
                <i class="fa-solid fa-backward-fast"></i>
              </span>
            </a>
          </li>

          <li class="page-item active" :class="(currentPage === elem) ? 'active' : '' " aria-current="page" v-for="(elem,index) in lastPage">
            <a class="page-link" href="#" @click.prevent="getProjects(elem)">{{ elem }}</a>
          </li>

          <li class="page-item">
            <a class="page-link" @click.prevent="getProjects(currentPage + 1)" href="#" aria-label="Next">
              <span aria-hidden="true">
                <i class="fa-solid fa-forward-fast"></i>
              </span>
            </a>
          </li>
        </ul>
      </nav>


    </div>
  </div>
</template>

<style>

li{
  list-style-type: none;
}
</style>
