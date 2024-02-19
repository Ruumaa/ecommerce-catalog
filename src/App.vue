<script>
import MenPage from './components/MenPage.vue';
import UnavailablePage from './components/UnavailablePage.vue';
import WomenPage from './components/WomenPage.vue';

export default {
    components: { MenPage, WomenPage, UnavailablePage },
    data(){
      return {
        index : 1,
        loading: false,
        products: Object
      }
    },
    methods: {
      async changeIndex(currentIndex) {
        this.index = (currentIndex % 20) + 1;
        await this.fetchProducts();
      },
      async fetchProducts(){
        try {
          this.loading = true
          const response = await fetch(`https://fakestoreapi.com/products/${this.index}`)
          const data = await response.json()
          this.products = data
          console.log(data)

        } catch (error) {
          console.error('Error when fetchProducts', error)
        } finally{
          this.loading = false
        }
      }
    },
    mounted(){
      this.fetchProducts()
    }
}
</script>

<template>
      <div v-if="loading" class="wrapper">
        <div class="circle"></div>
        <div class="circle"></div>
        <div class="circle"></div>
        <div class="shadow"></div>
        <div class="shadow"></div>
        <div class="shadow"></div>
    </div>
    <div v-else-if="products.category === `men's clothing`" class="main-container">
    <MenPage :productData="products"  v-if="products !== null && !loading" :changeIndex="changeIndex" :loading="this.loading"/>
   </div>
   <div v-else-if="products.category === `women's clothing`" class="main-container">
   <WomenPage :productData="products"  v-if="products !== null && !loading" :changeIndex="changeIndex" :loading="this.loading"/>
   </div>
   <div v-else class="main-container">
   <UnavailablePage :index="index" :changeIndex="changeIndex"/>
   </div>

</template>

<style>
@import 'assets/style/page.css'
</style>