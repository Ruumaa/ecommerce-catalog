<script>
export default {
    props:{
        productData: Object,
        changeIndex: Function,
        loading: Boolean
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
    </div>
     <main class="bg bg-women-main" v-else></main>
    <div class="card">
      <div class="image-container">
        <img class="image-content" :src="productData.image"/>
      </div>
      <div class="text-container">
        <div class="title title-women">{{ productData.title }}</div>
        <div class="category-rating-container">
          <p  class="category-title ">
            {{ productData.category}}
          </p>
          <div class="rating" v-if="productData.rating !== undefined && productData.rating !== undefined">
            {{ productData.rating.rate }}
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
        <div class="price price-women">${{ productData.price }}</div>
        <div class="button-container women-page">
             <button class="buy-button bg-women border-button-women">Buy Now</button>
             <button @click="changeIndex(productData.id)" class="next-button text-women border-button-women">Next Product</button>
        </div>
      </div>
    </div>
</template>
<style></style>