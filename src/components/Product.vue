<template>
  <v-card class="mx-auto my-5" max-width="600">
    <v-card-item :prepend-avatar="product.thumbnail_url">
      <div>
        <div class="text-h6 mb-1">{{ product.label }}</div>
        <div class="text-caption text-justify my-3">
          {{ product.description }}
        </div>
      </div>
    </v-card-item>

    <v-card-actions class="d-flex mb-6 justify-space-around">
      <v-card-item>
        <div>{{ product.price / 100 }}€</div>
      </v-card-item>
      <v-btn class="bg-secondary" @click="add()"> Ajouter au panier </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
import useCartStore from "../store/cart";

export default {
  name: "Product",
  props: {
    product: [],
  },

  data() {
    return {
      cartStore: useCartStore(),
    };
  },

  methods: {
    add() {
      this.cartStore.addItem(this.product);
    },
  },
};
</script>
