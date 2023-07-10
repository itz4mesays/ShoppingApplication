<template>
    <ul class="list-group">
        <li class="list-group-item" v-for="item in items" :key="item.id">
            {{ item.title }} - ${{ item.price }}

            <button class="btn badge btn-danger float-right">Remove from Cart</button>
        </li>
    </ul>
</template>

<script>
    export default {
        name: 'CartList',
        props: ['items']
    }
</script>

<style scoped>

</style>