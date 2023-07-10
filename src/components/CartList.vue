<template>
    
    <div>
        <ul class="list-group">
            <h5 class="text-muted">My Cart Items</h5>
            <li class="list-group-item" v-for="item in items" :key="item.id">
                {{ item.title }} - ${{ item.price }}

                <button @click="$emit('delete-from-cart', item)" class="btn badge btn-danger float-right">Remove from Cart</button>
            </li>
        </ul>


        <div class="card p-3 my-5">
            <h5 class="text-center">${{ total }}</h5>
        </div>

        <button :disabled="items.length === 0" @click="$emit('pay')" class="btn btn-primary form-control">Pay Now</button>


    </div>

</template>

<script>
    export default {
        name: 'CartList',
        props: ['items'],
        computed: {
            total() {
                return this.items.reduce(
                    (accumulator, item) => accumulator + Number(item.price), 0
                );
            }
        }
    }
</script>

<style scoped>

</style>