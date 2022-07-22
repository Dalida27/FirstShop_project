<template>
  <div>
    <div class="bg-gray-500 text-white fixed w-full top-0 left-0 z-10">
      <div class="container mx-auto">
        <div class="flex items-center justify-between py-3 px-0 lg:px-10">
          <p class="text-2xl font-bold">ShopName</p>
          <div>
            <RouterLink class="font-semibold text-xl pl-5 lg:pl-0 hover:text-black mr-5 pr-5" to="/">Home</RouterLink>
            <RouterLink
              class="font-semibold text-xl pl-5 lg:pl-0 hover:text-black"
              to="/products"
            >Products</RouterLink>
          </div>
          <div class="flex items-center">
            <RouterLink to="/cart" class="text-lg font-semibold font-lg hover:text-black">Cart</RouterLink>
            <p
              class="text-lg font-semibold font-lg pl-3 ease-in-out"
              data-bs-toggle="modal" data-bs-target="#exampleModal"
            >Sign In</p>
          </div>
        </div>
      </div>
    </div>
        <!-- Modal -->
    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <button class="w-full text-gray-500 py-2 rounded-lg font-semibold text-lg border mr-1">Sign In</button>
            <button class="w-full text-gray-500 py-2 rounded-lg font-semibold text-lg border ml-1">Sign Up</button>
          </div>
          <div class="modal-body">
            <form action="">
              <input class="border p-2 w-full block rounded-md my-4" placeholder="Email" type="text">
              <input class="border p-2 w-full block rounded-md my-4" placeholder="Пароль" type="password">
              <p class="hover:cursor-pointer bg-oran rounded-lg w-full text-center py-2 text-white uppercase font-semibold">Enter</p>
            </form>
            <!-- <form  action="">
              <input class="border p-2 w-full block rounded-md my-4" placeholder="Имя" type="text">
              <input class="border p-2 w-full block rounded-md my-4" placeholder="Фамилия" type="text">
              <input class="border p-2 w-full block rounded-md my-4" placeholder="Email" type="text">
              <input class="border p-2 w-full block rounded-md my-4" placeholder="Номер телефона" type="number">
              <input class="border p-2 w-full block rounded-md my-4" placeholder="Пароль" type="password">
              <input class="border p-2 w-full block rounded-md my-4" placeholder="Подтвердите пароль" type="password">
              <p class="hover:cursor-pointer bg-oran rounded-lg w-full text-center py-2 text-white uppercase font-semibold">Регистрация</p>
            </form> -->
          </div>
          <div class="modal-footer text-center">
            <button type="button" class=" mx-auto block w-1/2 font-semibold rounded-md text-sm p-2 text-white bg-gray-500" data-bs-dismiss="modal">Close</button>
          </div>
        </div>
      </div>
    </div>
    <RouterView />
  </div>
</template>

<script>
import { createClient, provideClient } from '@urql/vue';
export default {
  setup() {
    const client = createClient({
      url: 'http://38.242.229.113:8055/graphql',
    });
    provideClient(client)
  }
}
</script>

<style>
</style>
