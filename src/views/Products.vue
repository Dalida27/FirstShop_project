<template> 
  <div> 
    <div class="container mx-auto lg:mt-20 mt-24"> 
    <div> 
      <p>{{ searchString }}</p> 
      <div class="w-full"> 
        <p class="mt-3 text-xl pb-3 font-semibold text-gray-500">Search:</p>
        <input class=" w-1/3 border border-black p-1 rounded-md" type="text" placeholder="Search..." v-model="searchString" /> 
      </div> 
      <p class="mt-3 text-xl pb-3 font-semibold text-gray-500">Filtering: <span>&#8645;</span> </p>
      <div class="flex items-center">
       <div class="flex items-center">
          <p class="pr-3">Min Price: </p> 
          <input class=" w-1/2 border border-black p-1 rounded-md" type="text" placeholder="min" v-model.number="min" /> 
       </div> 
        <div class="flex items-center">
          <p class="pr-3">Max Price:</p> 
          <input class=" w-1/2 border border-black p-1 rounded-md" type="text" placeholder="max" v-model.number="max" /> 
        </div> 
      </div> 
    </div> 
    <div v-if="fetching">Loading...</div> 
    <div v-else-if="error">Oh no... {{ error }}</div> 
    <div v-else> 
      <div v-if="data"> 
        <div class="lg:flex lg:flex-wrap w-full lg:justify-between block lg:w-full "> 
          <div 
          v-for="p in data.products" 
          :key="p.id" 
          class="mb-3 mt-5 lg:w-1/3 w-full" 
        > 
          <div class="block"> 
             <img @click="move(p.id)"  class="lg:w-3/5 w-full mx-auto hover:border border-gray-500" :src="'http://38.242.229.113:8055/assets/' + p.image.id" alt=""> 
            <div> 
              <p class="text-lg font-semibold text-center pt-3">{{ p.title }}</p> 
              <div class="text-center mt-3">
                <button @click="addToCart(p)" class="text-gray-500 font-semibold text-lg border-2 border-gray-500 p-2 rounded-full hover:bg-gray-500 hover:text-white">Добавить в корзину</button>
              </div>
            </div> 
          </div> 
        </div> 
        </div> 
      </div> 
        <div class="text-center"> 
          <button class="text-xl font-lg text-white bg-gray-500 p-3 border rounded-md mb-10" @click="limit+=10">Show more</button> 
        </div> 
    </div> 
    </div> 
  </div> 
</template> 
 
<script> 
import { useQuery, gql } from "@urql/vue"; 
import { useRouter } from "vue-router"; 
import { ref } from "@vue/reactivity"; 
import { addToCart } from '@/utils/cart'
export default { 
  setup() { 
    const limit = ref(10); 
    const router = useRouter(); 
    const searchString = ref(null); 
    const min = ref(0); 
    const max = ref(10000000); 
    const getProductsQuery = gql` 
      query ($search: String, $min: Float, $max: Float, $limit: Int! = 10) { 
        products( 
          search: $search 
          filter: { 
            _and: [{ price: { _gte: $min } }, { price: { _lte: $max } }] 
          } 
          limit: $limit 
        ) { 
          id 
          title 
          price 
          description 
          image { 
            id 
          } 
        } 
      } 
    `; 
    const move = (id) => router.push("/products/" + id); 
    const getProducts = useQuery({ 
      query: getProductsQuery, 
      variables: { search: searchString, min, max, limit }, 
    }); // TODO: rename to products 
    return { 
      fetching: getProducts.fetching, 
      data: getProducts.data, 
      error: getProducts.error, 
      addToCart,
      move, 
      searchString, 
      min, 
      max, 
      limit 
    }; 
  }, 
}; 
</script> 
 
<style scoped></style>
