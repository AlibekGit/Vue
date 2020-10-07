<template>
    <div class="v-cart">
        <router-link :to="{name: 'catalog'}">
            <div class="link_cart">Back to Catalog</div>
        </router-link>
        <h1>Cart</h1>
        <p v-if="!cart_data.length">Your cart is empty</p>
        <v-cart-item
            v-for="(item, index) in cart_data"
            :key="item.article"
            :cart_item_data="item"
            @deleteFromCart="deleteFromCart(index)"
            @increment="increment(index)"
            @decrement="decrement(index)"
        />
        <div class="total-cost">
            <p class="total-cost__name">Total : ${{cartTotalCost}} </p>

        </div>
    </div>
</template>

<script>

    import vCartItem from './v-cart-item'
    import {mapActions} from 'vuex'


    export default {
        name: "v-cart",
        components:{
            vCartItem
        },
        props:{
            cart_data:{
                type:Array,
                default() {
                    return [];
                }
            }
        },
        methods:{
            ...mapActions([
                'DELETE_FROM_CART',
                'DECREMENT_CART_ITEM',
                'INCREMENT_CART_ITEM'
            ]),
            increment(index){
                this.INCREMENT_CART_ITEM(index)
            },
            decrement(index){
                this.DECREMENT_CART_ITEM(index)
            },
            deleteFromCart(index){
                this.DELETE_FROM_CART(index)
            }
        },
        computed:{
            cartTotalCost(){
                // let result = []
                // if(this.cart_data.length){
                //     for(let item of this.cart_data){
                //         result.push(item.price*item.quantity)  ;
                //     }
                //     result =    result.reduce(function (sum,el) {
                //         return sum+el;
                //     })
                //     return result;
                // }else {
                //     return 0;
                // }
                return this.cart_data.reduce((res, item) => res + item.price * item.quantity, 0)
            }
        }
    }


</script>

<style>
    .total-cost{
        position: fixed;
        bottom: 0;
        left: 0;
        right: 0;
        padding: 20px;
        display: flex;
        justify-content: center;
    }
    .total-cost__name{
        margin-right: 16px;
        background: #26ae68;
        color: #fff;
    }
    .v-cart{
        margin-bottom: 100px;
        text-align: center;
    }
</style>