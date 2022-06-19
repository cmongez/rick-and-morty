<template>
  <div
    id="carouselExampleFade"
    class="carousel slide carousel-fade mb-4 d-flex align-items-center"
    data-bs-ride="carousel"
  >
  <h1 class="subtitleRick w-100 p-5 h1 text-center">Tienda de Rick and Morty</h1>
    <div class="carousel-inner container__subtitleRick">
      
      <div class="carousel-item active">
        <img src="../assets/img/606024.jpg" class="d-block w-100" alt="..." />
      </div>
      <div class="carousel-item">
        <img src="../assets/img/633288.png" class="d-block w-100" alt="..." />
      </div>
      <div class="carousel-item">
        <img src="../assets/img/812062.png" class="d-block w-100" alt="..." />
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
  name: "Carrusel",
};
</script>

<style>
.container__subtitleRick {
  position: relative;
  filter: brightness(50%);
}
.subtitleRick {
  color: white;
  position: absolute;
  z-index: 2;
}
</style>