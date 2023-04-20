<template>
  <v-row class="d-flex justify-center my-5 mx-auto">
    <v-col cols="12" md="4">
      <h2 class="ma-auto">Accueil boutique</h2>
    </v-col>
    <v-col cols="12" md="4">
      <v-autocomplete
        prepend-icon="mdi-magnify"
        clearable
        label="Recherche par nom"
        :items="[
          '2 x Titre Unitaire',
          'Carnet 10 x Titres Unitaires',
          'Abonnement Mensuel',
          'Abonnement Annuel',
          'Abonnement Découverte',
          'Ticket Parking+Transport',
          'Carnet 10 x Ticket Parking+Transport',
        ]"
        v-model="searchByName"
        variant="underlined"
        class="ma-auto"
      ></v-autocomplete>
    </v-col>
  </v-row>
  <div v-for="product in products" v-bind:key="product.id">
    <Product
      :product="product"
      v-if="product.label.includes(searchByName) || !searchByName"
    />
  </div>
</template>

<script>
import Product from "@/components/Product.vue";
import axios from "axios";
import useCartStore from "../store/cart";

export default {
  name: "Home",

  components: { Product },
  data() {
    return {
      cartStore: useCartStore(),
      products: [],
      searchByName: null,
    };
  },

  mounted() {
    this.getProducts();
  },

  methods: {
    getProducts() {
      axios({
        method: "get",
        url: `https://test-feed.airweb.workers.dev/products`,
      })
        .then((response) => {
          this.products = response.data;
        })
        .catch((erreur) => {
          console.log(erreur);
        });
    },
  },
};
</script>
