<template>
  <div class="mt-20">
    <div class="container mx-auto">
      <div class="border-b pb-3 border-gray-500 mb-5" v-for="(p, index) in cart" :key="p.id">
        <div class="flex w-1/2">
          <div class="w-1/2">
            <img class="w-3/4" :src="'http://38.242.229.113:8055/assets/' + p.image.id" alt="">
          </div>
          <div class="block">
            <p class="text-xl font-semibold text-gray-500">{{ p.title }}</p>
            <p class="text-lg mt-3 font-lg"><span class="text-gray-500 font-semibold pr-3">Price:</span>{{ p.price }}</p>
            <div class="flex mt-5">
              <button @click="deleteFromCartLocal(index)" class="border-2 border-gray-500 p-2 text-white bg-gray-500 font-semibold rounded-full hover:bg-gray-600 hover:border-gray-600">Delete from Cart</button>
              <button class="border-2 border-gray-500 p-2 text-gray-500 rounded-full font-semibold hover:text-white hover:bg-gray-500">Buy Now</button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <FooterComp />
  </div>
</template>

<script>
import { ref } from '@vue/reactivity';
import { deleteFromCart } from '../utils/cart'
import FooterComp from "../components/FooterComp.vue"
export default {
  components: {
    FooterComp
  },
  setup() {
    let cart = ref(JSON.parse(sessionStorage.getItem('cart')));
    const deleteFromCartLocal = (index) => {
      cart.value.splice(index,1)
      deleteFromCart(index)
    }
    return {
      cart,
      deleteFromCart,
      deleteFromCartLocal
    }
  },
};
</script>
