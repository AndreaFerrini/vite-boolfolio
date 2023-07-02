<template>
    <div>
        <nav class="navbar navbar-expand-sm" id="navbar-header">
              <div class="container">
                <img src="/AndFer.png" alt="" srcset="" href="">
                <div class="collapse d-flex justify-content-end align-items-center" id="collapsibleNavId">
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
    color: rgb(0,42,47);
}

.nav-link{
    font-size: 20px;
}

#collapsibleNavId .nav-link:hover {
    background-color: rgb(0,42,47);
    color: rgb(0,232,242);
}

img{
    width: 150px;
    height: 100px;
}
</style>