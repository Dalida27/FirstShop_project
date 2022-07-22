<template> 
  <div>
    <div class="container mx-auto w-4/6 lg:mt-20 mt-24"> 
      <div v-if="fetching"> 
        Loading... 
      </div> 
      <div v-else-if="error"> 
        Oh no... {{ error }} 
      </div> 
      <div v-else>
        <div v-if="data"> 
          <div> 
           <div class="lg:flex block"> 
             <div class="lg:w-1/3 w-full">
               <img class="w-full" :src="'http://38.242.229.113:8055/assets/' +  data.products_by_id.image.id" alt="">
              </div> 
              <div class="block ml-20 bg-white"> 
                <p class="lg:text-3xl text-lg font-semibold">{{ data.products_by_id.title }}</p> 
                <div class="my-5">
                  <p class="text-2xl text-gray-500 font-semibold">Description: </p>
                   <p class="font-semibold text-xl pt-3">{{ data.products_by_id.description }}</p> 
                </div>
                <div class="my-5">
                  <p class="text-2xl text-gray-500 font-semibold">Price: </p>
                  <p class="font-semibold text-xl">{{ data.products_by_id.price }}</p> 
                </div>
                <hr class="mt-5">
                <div class="w-3/4">
                  <p class="mt-3 font-semibold text-lg">Бесплатная экспресс доставка за 2 часа по Алматы и Нур-Султан Официальная гарантия: 12 месяцев</p>
                </div>
              </div> 
           </div> 
          </div> 
        </div> 
      </div> 
    </div> 
    <FooterComp />
  </div> 
</template> 
 
<script> 
import { useRoute } from "vue-router"; 
import { useQuery, gql } from "@urql/vue"; 
import FooterComp from "../components/FooterComp.vue"
export default { 
  components: {
    FooterComp
  },
  setup() { 
    const route = useRoute(); 
    const getProductQuery = gql` 
      query ($id: ID!) { 
        products_by_id(id: $id) { 
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

    const getProduct = useQuery({ query: getProductQuery, variables: { id: route.params.id } }); 
    return { 
      fetching: getProduct.fetching, 
      data: getProduct.data, 
      error: getProduct.error, 
    }; 
  }, 
};
</script> 

 
<style scoped></style>