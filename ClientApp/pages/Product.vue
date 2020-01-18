<template>
    <div class="page">
        <product-details v-if="product" :product="product" />
    </div>    
</template>

<script>
import axios from "axios";
import ProductDetails from "../components/product/Details.vue";

export default {
    name: "product",
    components: {
        ProductDetails
    },
    data() {
        return {
            product: null
        };
    },
    /*mounted() {
        const slug = this.$route.params.slug;

        fetch(`/api/products/${slug}`)
            .then(response => {
            return response.json();
            })
            .then(product => {
            this.product = product;
            });
    }*/
    methods: {
        setData(product) {
            this.product = product;
        }
    },
    beforeRouteEnter(to, from, next) {
        
        /*fetch(`/api/products/${to.params.slug}`)
            .then(response => {
                return response.json();
            })
            .then(product => {
                next(vm => vm.setData(product));
            });*/

        axios.get(`/api/products/${to.params.slug}`).then(response => {
            next(vm => vm.setData(response.data));
        });
    }
}
</script>

<style>

</style>
