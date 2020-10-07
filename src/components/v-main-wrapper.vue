<template>
    <div class="v-main-wrapper">
        <router-view></router-view>
<!--        <v-catalog-wrapper/>-->
<!--        <v-cart-->
<!--                v-if="CART.length"-->
<!--                :cart_data="CART"-->
<!--        />-->
    </div>
</template>


<script>
    // import vCatalogWrapper from './v-catalog-wrapper'
    // import vCart from './v-cart'
    import {mapGetters} from 'vuex'
    export default {
        name:'v-main-wrapper',
        components:{
            // vCart,vCatalogWrapper
        },
        props:{},
        data(){
            return{

            }
        },
        computed:{
            ...mapGetters([
                'CART'
            ])
        },
        methods:{},
        watch:{},

    }
</script>


<style>
    body{
        padding: 0;
        margin: 0;
        font-family: 'Montserrat', sans-serif;
    }
    .v-main-wrapper{
        display: flex;
        flex-direction: column;

    }
    @import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');
    img{
        width: 120px;
    }
</style>