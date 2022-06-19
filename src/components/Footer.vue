<template>
  <footer class="text-white bg-footer mt-4 pt-3 pb-3">
    <div
      class="
        d-flex
        flex-column flex-md-row
        justify-content-center justify-content-md-around
        align-items-center
      "
    >
      <SocialNetworks
        class="d-flex  justify-content-around align-items-center"
      />
      <div class="d-flex flex-column align-items-center mb-2">
        <div class="d-flex align-items-center pb-2">
          <p class="text-center m-0">Hecho con</p>
          <BeatingHeart class="mx-2" title="Amor" />
          <p class="m-0">
            en
            <span class="f-w-bold fst-italic text-success" title="Vue.js" >Vue</span>
          </p>
        </div>
        <p class="m-0">
          Creado por
          <a class="text-white font-weight-bold" href="https://cmongez.github.io/portafolio" title="César Mongez" target="_blank"
            >César Mongez</a
          >
        </p>
      </div>
      <p class="text-center m-0">Copyright © 2022</p>
    </div>
  </footer>
</template>

<script>
import SocialNetworks from "@/components/SocialNetworks.vue";
import BeatingHeart from "@/components/animations/BeatingHeart.vue";
export default {
  name: "Footer",
  components: {
    SocialNetworks,
    BeatingHeart,
  },
};
</script>

<style lang="scss" scoped>
footer {
  background-color: black;
}
p{
  color:#A3ABB2
}
</style>