<template>
    <div class="v-catalog-item">
        <img :src="require( '../assets/'+product_data.image )" alt="img">
        <p>Name of product:{{product_data.name}} </p>
        <p>Price : ${{product_data.price}}</p>
        <button @click="addCart">add to cart</button>
    </div>
</template>

<script>
    export default {
        name: "v-catalog-item",
        props:{
            product_data: {
                type:Object,
                default(){
                    return{}
                }
            }
        },

        methods:{
            addCart(){
                this.$emit('addCart', this.product_data)
            }
        }

    }
</script>

<style>
    .v-catalog-item{
        padding: 20px;
        margin-top: 10px;
        display: flex;
        flex-direction: column;
        flex-basis: 25%;
        align-items: center;
        box-shadow: 0px 0px 8px 0px #eaeaea;
    }
</style>