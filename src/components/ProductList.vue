<template>
   
   <div class="card my-5">
        <div class="card-body">
            <img :src="product.thumbnail" class="card-img-top product-image" alt="#">
            
            <h5 class="card-title text-center mt-3">{{ product.title }}</h5>
            
            <p class="text-center my-2">{{ product.description }}</p>
            
            <p class="card-text text-muted display-5">${{ Number(product.price).toFixed(2) }}</p>

            <p class="text-muted">Category: {{ product.category }}</p>

            <button :disabled="isItemInCart" @click="$emit('add-to-cart', product)" class="btn btn-primary">
                {{ isItemInCart ? 'Added to Cart' : ' Add to Cart' }}
            </button>
            
        </div>
    </div>
    
</template>

<script>
    export default {
        name: 'ProductList',
        props: ['product', 'isItemInCart']
    }
</script>

<style scoped>
    .product-image {
        height: 250px
    }
</style>