<template>
  <div id="app" class="d-flex min-vh-100 flex-column align-items-stretch">
    <Navbar />

    <router-view class="flex-grow-1"/>
    <Footer />
  </div>
</template>
<script>
import Navbar from "@/components/Navbar.vue";
import Footer from "@/components/Footer.vue";

export default {
  components: {
    Navbar,
    Footer,
  },
};
</script>


<style lang="scss">
#app{
  background-color: #FFFCF2;
}
.bg-orange,.btn-danger:hover{
  background-color:  #EB5E28;
  
}
.btn-danger:hover{
  background-color:  #e0480c;
}

.btn-danger{
  background-color:  #EB5E28;
  border:#EB5E28;
}
.nav-item:hover{
  background-color: #e0480c;
  color:white;
}
a,a:link,a:visited{
  color:white
}
</style>
