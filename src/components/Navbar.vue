<template>
  <nav class="navbar navbar-expand-xl navbar-dark bg-secondary fixed-top">
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0 ">
        
        <li class="nav-item">
            <router-link to="/" class="nav-link active"><i class="fas fa-home"></i> Anasayfa </router-link>
          
        </li>
        <li class="nav-item">
        <router-link to="/favorites" class="nav-link"><i class="fas fa-heart"></i> Favoriler</router-link>
      
        </li>
        <li class="nav-item">
        </li>
      </ul>
    </div>    
  </nav>
</template>


<style scoped>

a:hover{
  color: #BB2D3B !important;
}
</style>
