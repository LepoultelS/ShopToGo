<template>
  <h2 class="ma-12" v-if="cartStore.items.length <= 0">
    Votre panier est vide
  </h2>
  <v-row class="ma-12">
    <h2 class="ma-auto" v-if="cartStore.items.length > 0">
      Votre panier ({{ cartStore.totalItems }})
    </h2>
  </v-row>
  <v-card class="mx-auto my-5" max-width="600">
    <v-table v-if="cartStore.items.length > 0">
      <thead>
        <tr>
          <th class="">Produit</th>
          <th class="">Prix</th>
          <th class="">Qté(s)</th>
          <th class=""></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in cartStore.items" :key="item.id">
          <td class="dLabel">{{ item.label }}</td>
          <td>{{ item.price / 100 }}€</td>
          <td>{{ item.count }}</td>
          <td>
            <v-btn
              class="text-none ml-n10"
              flat
              density="compact"
              @click="remove(item)"
            >
              <v-icon>mdi-delete</v-icon>
            </v-btn>
          </td>
        </tr>
      </tbody>
      <tfoot>
        <tr>
          <th class="text-left">Total</th>
          <th class="text-left">{{ cartStore.totalCost / 100 }}€</th>
          <th class="text-left">{{ cartStore.totalItems }}</th>
          <th></th>
        </tr>
      </tfoot>
    </v-table>
    <v-row v-if="cartStore.items.length > 0">
      <v-btn class="mx-auto my-12" @click="alert()">Passer commande</v-btn>
    </v-row>
  </v-card>
</template>
<script>
import useCartStore from "../store/cart";

export default {
  name: "Cart",

  data() {
    return {
      cartStore: useCartStore(),
    };
  },

  methods: {
    remove(item) {
      this.cartStore.removeItem(item);
    },
    alert() {
      alert("Fonctionnalité en cours de développement");
    },
  },
};
</script>

<style>
.dLabel {
  font-size: 0.8em;
}
</style>
