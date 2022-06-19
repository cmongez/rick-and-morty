<template>
<div class="">
  <nav class="navbar navbar-expand-lg navbar-light bg-orange">
  <div class="container">
    <router-link to="/" class="navbar-brand text-white" >BOOTCAMP VUE</router-link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <a class="nav-link" href=""><router-link to="/home">Home</router-link></a>
        </li>
 
        
        
        
      </ul>
    </div>
  </div>
</nav>
</div>
    
</template>

<script>

import CartDetail from'@/components/CartDetail.vue'

export default {
  
  components:{
    CartDetail,
  },
  
  
}
</script>

<style>

</style>