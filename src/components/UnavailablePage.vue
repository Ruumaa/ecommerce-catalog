<script>
export default {
    props:{
        index: Number,
        changeIndex: Function,
    }
}
</script>

<template>
     <main class="bg bg-unavailable-main"></main>
    <div class="card">
        <div class="unavailable-container">
            <div class="inner-container">
                <h5 class="unavailable-title">This product is unavailable to show</h5>
                <button @click="changeIndex(index)" class="unavailable-button">Next product</button>
            </div>
        </div>
    </div>
</template>
<style></style>