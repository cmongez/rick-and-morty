<template>
  <div class="heart"></div>
</template>

<script>
export default {};
</script>

<style>
body {
  display: flex;
  justify-content: center;
  align-items: center;

}
:root {
  --heigth: 12.5px;
  --color: red;
}
.heart {
  height: var(--heigth);
  width: var(--heigth);
  background-color: var(--color);
  transform: rotate(45deg);
  animation: latir 0.5s infinite ease-in-out alternate;
}
.heart::before,
.heart::after {
  content: "";
  height: var(--heigth);
  width: var(--heigth);
  background-color: var(--color);
  display: block;
  position: absolute;
  border-radius: 50%;
  transform: translateY(-6.75px);
}
.heart::after {
  transform: translateX(-6.75px);
}
@keyframes latir {
  100% {
    transform: rotate(45deg) scale(1.2);
  }
}
</style>