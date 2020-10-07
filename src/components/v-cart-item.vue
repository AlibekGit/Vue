<template>
    <div class="v-cart-item">
        <img :src="require( '../assets/'+cart_item_data.image )" alt="img">
        <div class="v-cart-item__info">
            <p>Name : {{cart_item_data.name}}</p>
            <p>Price : ${{cart_item_data.price}}</p>
            <p>Article : {{cart_item_data.article}}</p>
        </div>
        <div class="v-cart-item__quantity">
            <span>
                <p>Qty: </p>
                <span class="click" @click="decrementItem">-</span>
                {{cart_item_data.quantity}}
                <span class="click" @click="incrementItem">+</span>
            </span>
        </div>
        <button @click="deleteFromCart">Delete</button>
    </div>
</template>

<script>

    export default {


        name: "v-cart-item",
        props:{
            cart_item_data:{
                type:Object,
                default(){
                    return {}
                }
            }
        },
        methods:{

            incrementItem(){
                this.$emit('increment')
            },
            decrementItem(){
                this.$emit('decrement')
            },
            deleteFromCart(){
                this.$emit('deleteFromCart')
            }
        },
        mounted(){
            this.$set(this.cart_item_data, 'quantity', 1)
        },


    }
</script>

<style>
    .click{
        cursor: pointer;
    }
    .v-cart-item{
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: nowrap;
        box-shadow: 0px 0px 8px 0px #eaeaea;
        margin-top: 20px;
        padding: 20px;
    }
</style>