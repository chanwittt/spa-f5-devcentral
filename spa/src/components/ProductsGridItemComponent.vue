<template>
  <div class="product-item">
    <img :src="config.apiUrl + product.imageUrl" />
    <h3 class="product-name">
      {{ product.name }}
    </h3>
    <p class="product-price">${{ product.price }}</p>
    <router-link :to="'/products/' + product.id">
      <button id="view-details">View Details</button>
    </router-link>
  </div>
</template>

<script lang="ts">
import { defineComponent, type PropType } from "vue"
import type { Product } from "../types"
import { loadStorage } from "@/utils/Storage"

export default defineComponent({
  name: "ProductsGridItemComponent",
  props: {
    product: {
      type: Object as PropType<Product>,
      required: true,
    },
  },
  data() {
    return {
      config: {} as any,
    }
  },
  async created() {
    this.config = loadStorage()
  },
})
</script>

<style scoped>
.product-item {
  align-items: center;
  border-radius: 8px;
  box-shadow: 0px 2px 5px #888;
  display: flex;
  flex-direction: column;
  margin-bottom: 2%;
  padding: 20px;
  position: relative;
  width: 32%;
}

.product-name {
  margin-bottom: 0;
  height: 15%;
}

img {
  height: 200px;
  width: 200px;
}

a {
  width: 100%;
}

button {
  width: 100%;
}
</style>
