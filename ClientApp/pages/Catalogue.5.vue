<template>
    <b-container fluid class="page">
        <b-row>
            <b-col cols="3">
                <filters v-if="filters.brands.length" :filters="filters" />
            </b-col>            
            <b-col cols="9">
                <div class="mt-4 clearfix">
                    <product-sort class="float-right" />
                </div>
                <product-list v-if="products.length" :products="sortedProducts" />
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
import ProductList from "../components/catalogue/ProductList.vue";
import axios from "axios";
import Filters from "../components/catalogue/Filters.vue";
import ProductSort from "../components/catalogue/ProductSort.vue";

export default {
    name: "catalogue",
    components: {
        Filters,
        ProductSort,
        ProductList        
    },
    data() {
        return {
            products: [],
            filters: {
                brands: [],
                capacity: [],
                colours: [],
                os: [],
                features: []
            }
        };
    },
    computed: {
        sort() {
            return this.$route.query.sort || 0;
        },
        sortedProducts() {
            switch (this.sort) {
            case 1:
                return this.products.sort((a, b) => {
                return b.price > a.price;
                });
                break;
            case 2:
                return this.products.sort((a, b) => {
                return a.name > b.name;
                });
                break;
            case 3:
                return this.products.sort((a, b) => {
                return b.name > a.name;
                });
                break;
            default:
                return this.products.sort((a, b) => {
                return a.price > b.price;
                });
            }
        }
    },
    /*mounted() {
        fetch("/api/products")
            .then(response => {
            return response.json();
            })
            .then(products => {
            this.products = products;
            });
    },*/
    methods: {
        setData(products, filters) {
            this.products = products;
            this.filters = filters;
        }
    },
    beforeRouteEnter(to, from, next) {        
        /*fetch("/api/products")
            .then(response => {
                return response.json();
            })
            .then(products => {
                next(vm => vm.setData(products));
            });*/
        axios
            .all([
                axios.get("/api/products", { params: to.query }),
                axios.get("/api/filters")
            ])
            .then(
                axios.spread((products, filters) => {
                    next(vm => vm.setData(products.data, filters.data));
                })
            );
    },
    beforeRouteUpdate(to, from, next) {
        axios.get("/api/products", { params: to.query }).then(response => {
            this.products = response.data;
            next();
        });
    }
}
</script>

<style>

</style>
