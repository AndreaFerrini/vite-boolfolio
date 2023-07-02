<template>
    <div>
        <nav class="navbar navbar-expand-sm" id="navbar-header">
              <div class="container">
                <img src="/AndFer.png" alt="" srcset="" href="">
                <button class="navbar-toggler d-lg-none" type="button" data-bs-toggle="collapse" data-bs-target="#collapsibleNavId" aria-controls="collapsibleNavId"
                    aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="collapsibleNavId">
                    <ul class="navbar-nav me-auto mt-2 mt-lg-0">
                        <li class="nav-item">
                            <router-link class="nav-link active" :to="{name: 'home'}" aria-current="page">Home</router-link>
                        </li>
                        <li class="nav-item">
                            <router-link class="nav-link" :to="{name: 'projects'}">Blog</router-link>
                        </li>
                    </ul>
                </div>
          </div>
        </nav>
        
    
    </div>
</template>

<script>
export default {
    name: "AppHeader", 
    data () {
        
        return{

        }
    }
}
</script>


<style>

#navbar-header{
    background-color: rgb(0,232,242);
    color: rgb(0,72,78);
}

img{
    width: 150px;
    height: 100px;
}
</style>