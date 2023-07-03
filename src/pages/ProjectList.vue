<script>
import axios from "axios";

export default{
    name: "ProjectList",
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

      axios.get(`${this.baseUrl}/api/projects`, {
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

  <div class="container mt-3">
    <h1 class="text-center mb-3">Ecco i miei progetti</h1>
    <div class="row main">
      <div class="col-6" v-for="(elem,index) in projects" :key="index">
        <div class="card text-center">
          <img class="card-img-top" :src="`${baseUrl}/storage/${elem.cover_image}`" alt="Title" id="img-projects">
          <div class="mt-2">
            <router-link :to="{ name: 'project', params: { slug: elem.slug } }" >
                <h4 class="card-title">
                    {{elem.title}}
                </h4>
            </router-link>
            
            <p class="card-text">{{elem.content}}</p>


            <div>
              <h5>Types</h5>
              <span v-if="elem.type">{{ elem.type.name}}</span>
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
      <nav aria-label="Page navigation" class="mt-3" id="change-page">
        <ul class="pagination" id="pagination-control">
          <li class="page-item">
            <a class="page-link" @click.prevent="getProjects(currentPage - 1)" href="#" aria-label="Previous">
              <span aria-hidden="true">
                <i class="fa-solid fa-backward-fast"></i>
              </span>
            </a>
          </li>

          <li class="page-item" :class="(currentPage === elem) ? 'active' : '' " aria-current="page" v-for="(elem,index) in lastPage">
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

.fa-solid{
    color: rgb(0,232,242);
}

.card{
    color: rgb(0,42,47);
}

#img-projects{
    width: 100%;
    height: 60%;
}


a{
    text-decoration: none;
    color: rgb(0,232,242);
}

ul{
    padding-left: 0;
}

li{
  list-style-type: none;
}

.page-link{
    color: rgb(0,232,242);
    background-color: rgb(0,42,47);
}
</style>