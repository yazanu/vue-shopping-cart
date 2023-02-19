<template>
    <div>
        <Master>
            <Loader v-show="isLoad"/>
            <div class="container" v-show="!isLoad">
            <div class="row">
                <div class="col-md-4" v-for="product in products" :key="product.id">
                    <div class="card p-3 m-3">
                        <div class="card-header">{{product.title}}</div>
                        <div class="card-body">
                            <img :src="product.thumbnail" alt="Product Myanmar" width="100%" height="200px">
                        </div>
                        <div class="card-footer">
                            <span>Price : <small>${{product.price}}</small></span>
                            <a @click="addToCart(product)" class="btn btn-sm btn-dark" style="float: right;">Add to cart</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        </Master>
    </div>
</template>

<script>
import Master from '../Layout/Master.vue'
import Loader from '../Component/Loader.vue'
import axios from 'axios'
    export default {
       name: "Product" ,
       components: {Master, Loader},
       data() {
           return {
               isLoad: true,
               products: []
           }
        },
        created() {
            axios.get('https://dummyjson.com/products')
            .then(res => {
                this.products = res.data.products
                this.isLoad = false
            })
        },
        methods: {
            addToCart(p){
                var cart = this.$root.cart
                var isInCart = cart.find(v=>{ //find product in cart in order to not multiple of the same product
                console.log('same');
                    return v.id == p.id
                })
                if(isInCart){
                    isInCart.qty++
                }else{
                    cart.push({...p, qty: 1})
                }
            }
        },
    }
</script>
