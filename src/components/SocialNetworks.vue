<template>
  <ul class="socialNetworks d-flex justify-content-around align-items-center  mt-2">
    <li class="socialNetworks__item">
      <a
        href="https://www.linkedin.com/in/cmongez/"
        target="_blank"
        class="socialNetworks__link"
        ><img
          class="socialNetworks__img img-fluid"
          src="../assets/img/linkedin.png"
          title="Perfil de LinkedIn"
          alt="Icono LinkedIn"
      /></a>
    </li>
    <li class="socialNetworks__item">
      <a
        href="https://github.com/cmongez"
        target="_blank"
        class="socialNetworks__link"
        ><img
          class="socialNetworks__img img-fluid"
          src="../assets/img/github.png"
          title="Perfil de GitHub"
          alt="Icono GitHub"
      /></a>
    </li>
    <li class="socialNetworks__item">
      <a href="https://cmongez.github.io/portafolio" target="_blank" class="socialNetworks__link"
        ><img title="Portafolio"
          class="socialNetworks__img img-fluid"
          src="../assets/img/portfolio.png"
          alt="Icono codigo portafolio"
      /></a>
    </li>
  </ul>
</template>

<script>
export default {
  name: "SocialNetworks",
};
</script>

<style lang="scss" scoped>
.socialNetworks {
    list-style: none;
    
    &__item{
    margin-left: 5px;
    margin-right: 5px;
    }
  &__img {
    min-width: 25px;
    max-width: 35px;
  }
}

</style>