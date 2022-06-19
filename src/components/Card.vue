<template>
  <CartDetail
    :totale="sumatoria"
    :cardACart="carrito"
    @removeAll2="onRemoveAll"
    @oneMore2="onOneMore"
    @oneLess2="onOneLess"
    @remove2="onRemove"
  />
  <Modal :modalProps="modal" />

  <div class="container-fluid mb-5">
    <div class="container w-75 d-flex">
      <input
        class="form-control me-2"
        v-model="filtro"
        type="text"
        placeholder="Buscar..."
        aria-label="Search"
      />
      <button class="btn btn-outline-success" type="submit">Search</button>
    </div>
    <div class="d-flex justify-content-end m-4">
      <button
        class="btn btn-success"
        href=""
        data-bs-toggle="modal"
        data-bs-target="#exampleModalCart"
      >
        Ver Carrito
      </button>
    </div>

    
    <div class="row justify-content-center ">
      <div
        class=" d-flex col-9 col-sm-4 col-md-3 col-lg-2 px-4 mb-2 pb-2"
        v-for="(item, index) in filtroNombres"
        :key="index"
      >
        <div class="card">
          <img
            class="card-img-top"
            v-bind:src="item.image"
            v-bind:alt="item.name"
          />
          <div class="card-body flex-grow-2">
            <h5 class="card-title text-center">{{ item.name }}</h5>
            <span class="mx-auto">Stock:{{ item.stock }}</span>
          </div>
          <div class="d-flex justify-content-center flex-wrap">
            <div class="d-flex justify-content-around w-100 mb-2">
              <button
                v-if="item.stock > 0"
                type="button"
                class="btn btn-success p-1"
                @click="addToCart(item.id)"
              >
                Comprar
              </button>
              <button
                v-else
                type="button"
                class="btn btn-outline-success p-1 disabled"
                @click="addToCart(item.id)"
              >
                Comprar
              </button>
              <button
                type="button"
                class="btn btn-danger p-1"
                data-bs-toggle="modal"
                data-bs-target="#exampleModal"
                @click="showMore(item)"
              >
                Detalles
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CartDetail from "@/components/CartDetail.vue";

import Modal from "@/components/Modal.vue";
export default {
  components: {
    Modal,
    CartDetail,
  },
  data() {
    return {
      carrito: [],
      producto: [],
      modal: {
        name: "",
        origin: "",
        status: "",
        gender: "",
        species: "",
      },
      filtro: "",
      sumatoria: 0,
    };
  },
  props: {
    resultProps: {
      type: Array,
      required: true,
    },
    favoritosProps: {
      type: Array,
    },
  },
  methods: {
    //Le envia los datos a el modal para mostrar detalles
    showMore(object) {
      this.modal = {
        name: object.name,
        origin: object.origin.name,
        status: object.status,
        gender: object.gender,
      };
      console.log(object);
    },
    //Realiza la suma de todos los productos que esten en el carrito
    totalCarrito() {
      this.sumatoria = 0;
      for (let i = 0; i < this.carrito.length; i++) {
        this.sumatoria += this.carrito[i].precio * this.carrito[i].cant;
      }
    },

    //Añade un producto al carrito
    addToCart(idAdd) {
      //Agrega el producto a un array vacio llamado producto
      this.producto = this.resultProps.find((item) => item.id === idAdd);
      //verifica si el producto ya esta en el carrito
      this.verificar = this.carrito.some((item) => item.id === idAdd);
      //Si no esta le agrega la propiedad cantidad y lo añade a el carrito
      if (!this.verificar) {
        this.producto.precio = 100;
        this.producto.cant = 1;
        this.producto.stock--;
        this.carrito.push(this.producto);
      } else {
        //Si ya se encuentra entonces solo suma uno mas y resta al stock
        if (this.producto.stock > 0) {
          this.producto.cant++;
          this.producto.stock--;
        } else {
          alert("No nos quedan mas producto de ese tipo");
        }

        this.totalCarrito();
      }
    },
    //Añade un producto mas desde la vista del carrito
    onOneMore(idMore) {
      let oneMoreFind = this.carrito.find((item2) => item2.id == idMore);
      if (oneMoreFind.stock > 0) {
        oneMoreFind.cant++;
        oneMoreFind.stock--;
      } else {
        alert("No nos quedan mas producto de ese tipo");
      }
      this.totalCarrito();
    },
    //Resta uno desde la vista de el carrito
    onOneLess(idLess) {
      let oneLessFind = this.carrito.find((item3) => item3.id == idLess);
      if (oneLessFind.stock >= 0) {
        oneLessFind.cant--;
        oneLessFind.stock++;
      } else {
        alert("No nos quedan mas producto de ese tipo");
      }
      if (oneLessFind.cant <= 0) {
        this.onRemove(idLess);
      }
      this.totalCarrito();
    },
    //Elimina un producto del carrito
    onRemove(idRemove) {
      let oneRemove = this.carrito.filter((item4) => item4.id !== idRemove);

      let oneRemoveCarrito = this.carrito.find((item5) => item5.id == idRemove);

      oneRemoveCarrito.stock += oneRemoveCarrito.cant;
      this.carrito = oneRemove;
      this.totalCarrito();
    },
    //Vacia el carrito
    onRemoveAll(idRemoveAll) {
      this.carrito.forEach((element) => {
        let perrito = this.resultProps.find((item4) => item4.id == element.id);
        perrito.stock += perrito.cant;
      });

      this.carrito = [];
      this.totalCarrito();
    },
  },
  //Buscador
  computed: {
    filtroNombres: function () {
      return this.resultProps.filter((item) => {
        return item.name.toLowerCase().match(this.filtro.toLowerCase());
      });
    },
  },
};
</script>

<style>
</style>