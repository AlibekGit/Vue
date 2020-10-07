<template>
    <div class="v-catalog">
        <v-catalog-item
                v-for="product in PRODUCTS"
                :key="product.article"
                v-bind:product_data="product"
                @addCart="addCart"
        />
    </div>
</template>

<script>

    import vCatalogItem from './v-catalog-item'
    import {mapActions,mapGetters} from 'vuex'


    export default {
        data(){
            return{

            }
        },
        components:{
            vCatalogItem
        },
        computed:{
          ...mapGetters([
              'PRODUCTS'
          ])
        },
        methods:{
            ...mapActions([
               'GET_PRODUCTS_FROM_API',
                'ADD_TO_CART'
            ]),
            addCart(data){
                this.ADD_TO_CART(data)
            }
        },
        mounted() {
          this.GET_PRODUCTS_FROM_API()

        },
        name: "v-catalog"
    }
</script>

<style>
    .v-catalog{
        display: flex;
        justify-content: space-around;
        flex-flow: row wrap;
        text-align: center;
    }
</style>