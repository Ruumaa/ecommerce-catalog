<script>
export default {
    props:{
        productData: Object,
        changeIndex: Function,
        loading: Boolean,
        refreshPage: Function
    },
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
        <span>Loading</span>
    </div>
     <main class="bg bg-men-main" v-else><img src="../assets/static/bg-pattern.svg" alt="pattern" class="pattern"></main>
    <div class="card" >
      <div class="image-container">
        <img class="image-content" :src="productData.image"/>
      </div>
      <div class="text-container">
        <div class="title title-men">{{ productData.title }}</div>
        <div class="category-rating-container">
          <p  class="category-title ">
            {{ productData.category }}
          </p>
          <div class="rating" v-if="productData.rating !== undefined && productData.rating !== undefined">
            {{productData.rating.rate}}
            <div v-for="i in 5" :key="i">
              <div v-if="i <= Math.round(productData.rating.rate)"  class="rating-icon rating-icon-filled-men rating-border-men">
              </div>
              <div v-else class="rating-icon rating-icon-empty rating-border-men"></div>
            </div>
          </div>
        </div>
        <div class="divider"></div>
        <div class="description">
          <p>{{ productData.description }}</p>
        </div>
        <div class="divider"></div>
        <div class="price price-men">${{ productData.price}}</div>
        <div class="button-container men-page">
            <button @click="refreshPage()" class="buy-button bg-men border-button-men">Buy Now</button>
            <button @click="changeIndex(productData.id)" class="next-button text-men border-button-men" >Next Product</button>
        </div>
      </div>
    </div>
</template>
<style>
@import '../assets/style/page.css'
</style>