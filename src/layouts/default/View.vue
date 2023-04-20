<template>
  <v-main class="bg-grey-lighten-3">
    <v-app-bar color="primary">
      <v-app-bar-title>
        <h2>ShopToGo</h2>
      </v-app-bar-title>

      <template v-slot:append>
        <v-btn to="/" class="text-none" stacked>
          <v-icon> mdi-store </v-icon>
          <v-tooltip activator="parent" location="bottom">Boutique</v-tooltip>
        </v-btn>
        <v-btn to="/cart" class="text-none" stacked>
          <v-badge :content="cartStore.totalItems" color="error">
            <v-icon>mdi-cart</v-icon>
          </v-badge>
          <v-tooltip activator="parent" location="bottom">Panier</v-tooltip>
        </v-btn>
      </template>
    </v-app-bar>
    <router-view />
  </v-main>
  <v-footer class="bg-grey-lighten-3 py-5">
    <v-row justify="center" no-gutters>
      <v-btn variant="text" class="mx-2"> CGU </v-btn>
      <v-btn variant="text" class="mx-2"> CGV </v-btn>
      <v-btn variant="text" class="mx-2"> About us </v-btn>
      <v-col class="text-center mt-4" cols="12">
        <p>
          {{ new Date().getFullYear() }} - Test technique pour la société Airweb - Par Stéphane Lepoultel
        </p>
      </v-col>
    </v-row>
  </v-footer>
</template>

<script>
import useCartStore from "../../store/cart";

export default {
  name: "View",

  data() {
    return {
      cartStore : useCartStore(),
      products: [],
      categories: [],
      searchByName: "",
    };
  },
};
</script>
