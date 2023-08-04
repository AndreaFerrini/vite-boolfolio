<script>
export default {
    name: "AppHeader", 
    data () {
        
        return{

        }
    }
}
</script>

<template>
    <div>
        <nav class="navbar navbar-expand-sm navbar-transparent" id="navbar-header">
              <div class="container">
                <img src="/AndFer.png" alt="" srcset="" href="">
                <div class="collapse d-flex justify-content-end align-items-center" id="collapsibleNavId">
                    <ul class="navbar-nav me-auto mt-2 mt-lg-0">
                        <li class="nav-item">
                            <router-link class="nav-link active pe-3" :to="{name: 'home'}" aria-current="page">Home</router-link>
                        </li>
                        <li class="nav-item pe-3">
                            <router-link class="nav-link" :to="{name: 'projects'}">Blog</router-link>
                        </li>
                        <li class="nav-item pe-3">
                            <a href="https://www.linkedin.com/in/andrea-ferrini-263384199/">
                                <button>
                                    <i class="fa-brands fa-linkedin"></i>
                                </button>
                            </a>
                        </li>
                        <li class="nav-item pe-3">
                            <a href="https://github.com/AndreaFerrini">
                                <button>
                                    <i class="fa-brands fa-github"></i>
                                </button>
                            </a>

                        </li>
                    </ul>
                </div>
          </div>
        </nav>
        
    
    </div>
</template>


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

.nav-item:hover{
    background-color: rgb(0,42,47);
    color: rgb(0,232,242);
}

button{
    margin-top: 10px;
    background-color: rgb(0,232,242);
    border: none;
    color: rgb(0,42,47);
}

button i{
    font-size: 25px;
}

img{
    width: 150px;
    height: 100px;
}
</style>