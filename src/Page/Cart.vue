<template>
    <div>
        <Master>
            <div class="container">
                <h1 class="my-3">Cart Page</h1>

                <table class="table table-striped">
                    <thead>
                        <tr>
                            <th>Name</th>
                            <th>Image</th>
                            <th>+ -</th>
                            <th>Qty</th>
                            <th>Price</th>
                            <th>Sub Total</th>
                        </tr>
                    </thead>
                    <tr v-for="product in cart" :key="product.id">
                        <td>{{product.title}}</td>
                        <td width="15%">
                            <img :src="product.thumbnail" alt="Product Myanmar" width="100%">
                        </td>
                        <td>
                            <button @click="addQty(product)" class="btn btn-sm btn-success bg-success">+</button>
                            <button @click="reduceQty(product)" class="btn btn-sm btn-danger bg-danger" style="margin-left: 10px">-</button>
                        </td>
                        <td>{{product.qty}}</td>
                        <td>{{product.price}}</td>
                        <td>{{product.qty * product.price}}</td>
                    </tr>
                </table>
            </div>
        </Master>
    </div>
</template>

<script>
import Master from '../Layout/Master.vue'
    export default {
       name: "Cart" ,
       components: {Master},
        data() {
           return {
               cart: []
           }
        },
        created() {
           this.cart = this.$root.cart
        },
        methods: {
            addQty(p){
                return p.qty++
            },
            reduceQty(p){
                return p.qty--
            },
        },
    }
</script>
