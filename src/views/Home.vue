<template>
  <div>
    <div class="container mx-auto mt-3">
      <div class="flex">
        <div
          id="carouselExampleControls"
          class="carousel slide w-full my-8 mr-5"
          data-bs-ride="carousel"
        >
          <div class="carousel-indicators">
            <button
              type="button"
              data-bs-target="#carouselExampleControls"
              data-bs-slide-to="0"
              class="active"
              aria-current="true"
              aria-label="Slide 1"
            ></button>
            <button
              type="button"
              data-bs-target="#carouselExampleControls"
              data-bs-slide-to="1"
              aria-label="Slide 2"
            ></button>
            <button
              type="button"
              data-bs-target="#carouselExampleControls"
              data-bs-slide-to="2"
              aria-label="Slide 3"
            ></button>
          </div>
          <div class="carousel-inner rounded-lg w-4/5 mx-auto">
            <div class="carousel-item active">
              <img src="../assets/1.webp" class="d-block w-full" alt="..." />
            </div>
            <div class="carousel-item">
              <img src="../assets/2.webp" class="d-block w-full" alt="..." />
            </div>
            <div class="carousel-item">
              <img
                src="../assets/3.webp"
                class="d-block w-full mx-auto"
                alt="..."
              />
            </div>
          </div>
          <button
            class="carousel-control-prev"
            type="button"
            data-bs-target="#carouselExampleControls"
            data-bs-slide="prev"
          >
            <i class="fas fa-chevron-left"></i>
            <p><span class="text-5xl font-semibold">&#60;</span></p>
          </button>
          <button
            class="carousel-control-next"
            type="button"
            data-bs-target="#carouselExampleControls"
            data-bs-slide="next"
          >
            <font-awesome-icon icon="faHatWizard" />
            <p><span class="text-5xl font-semibold">&#62;</span></p>
          </button>
        </div>
      </div>
      <div class="flex items-center justify-evenly">
        <div class="flex items-center">
          <img src="https://cdn0.ipoint.kz/AfrOrF3gWeDA6VOlDG4TzxMv39O7MXnF4CXpKUwGqRM/resize:fit:210:210:0/bg:f6f6f6/plain/s3://files/7/i-store-block-8-by-image-1.jpg@jpeg" alt="">
          <div class="block ml-4">
            <p class="text-xl font-semibold">AirPods.</p>
            <p class="py-3 text-lg text-gray-500">Никаких проводов.</p>
            <p class="text-lg dont-semibold text-blue-400">Купить <span class="text-blue-300 font-semibold">&#62;</span></p>
          </div>
        </div>
        <div class="flex items-center">
          <img src="https://cdn0.ipoint.kz/AfrOrF3gWeDA6VOlDG4TzxMv39O7MXnF4CXpKUwGqRM/resize:fit:210:210:0/bg:f6f6f6/plain/s3://files/7/main-catalog-banner-iphone-case.png@jpeg" alt="">
          <div class="block ml-4">
            <p class="text-xl font-semibold">Чехлы на iPhone 13.</p>
            <p class="py-3 text-lg text-gray-500">Только идеальные пары.</p>
            <p class="text-lg dont-semibold text-blue-400">Заказать <span class="text-blue-300 font-semibold">&#62;</span></p>
          </div>
        </div>
        <div class="flex items-center">
          <img src="https://cdn0.ipoint.kz/AfrOrF3gWeDA6VOlDG4TzxMv39O7MXnF4CXpKUwGqRM/resize:fit:210:210:0/bg:f6f6f6/plain/s3://files/7/main-catalog-panel-watch-banner.png@jpeg" alt="">
          <div class="block ml-4">
            <p class="text-xl font-semibold">AppleWatch.</p>
            <p class="py-3 text-lg text-gray-500">Технологии из будущего.</p>
            <p class="text-lg dont-semibold text-blue-400">Купить <span class="text-blue-300 font-semibold">&#62;</span></p>
          </div>
        </div>
      </div>
    </div>
    <FooterComp />
  </div>
</template> 

 
<script> 
import FooterComp from "../components/FooterComp.vue"
export default { 
  components: {
    FooterComp
  }
}; 
</script> 
 
<style>
.carousel-indicators {
  background: rgba(0, 0, 0, 0.7);
  width: fit-content;
  margin: 0;
  left: 50%;
  bottom: 1rem;
  transform: translateX(-50%);
  padding: 3px;
  border-radius: 90px;
}

.carousel-indicators button {
  width: 4px !important;
  height: 4px !important;
  border-top: none !important;
  border-bottom: none !important;
  border-radius: 100%;
  margin-left: 2px !important;
  margin-right: 2px !important;
}

.carousel-indicators button.active {
  width: 12px !important;
  border-radius: 90px;
  box-shadow: 1px 1px 2px rgb(0 0 0 / 90%);
}

.carousel-control-next,
.carousel-control-prev {
  width: fit-content;
  height: fit-content;
  background: #fff;
  padding: 1rem;
  border-radius: 100%;
  color: #000;
  top: 50%;
  transform: translateY(-50%);
  opacity: 0;
}

.carousel-control-next:focus,
.carousel-control-next:hover,
.carousel-control-prev:focus,
.carousel-control-prev:hover {
  color: #000;
}

.carousel:hover .carousel-control-next,
.carousel:hover .carousel-control-prev {
  opacity: 1;
}

.carousel-control-next {
  right: 1rem;
}

.carousel-control-prev {
  left: 1rem;
}
</style>