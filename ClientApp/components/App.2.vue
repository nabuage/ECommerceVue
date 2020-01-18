<template>        
    <div>
        
        <b-navbar toggleable="md" type="dark" variant="dark">
            <b-container>
                <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
                <b-navbar-brand to="/">PhoneShop</b-navbar-brand>
                <b-collapse is-nav id="nav_collapse">
                <b-navbar-nav>
                    <b-nav-item to="/products">Products</b-nav-item>
                </b-navbar-nav>
                </b-collapse>
            </b-container>
        </b-navbar>
        <h1>Welcome to Hands on Vue.js with ASP.NET Core!</h1>
        <p>
            The time is: {{ time }}
        </p>
        <p>
            The current users of our system are:
            <ul>
                <li v-for="user in users" :key="user.userName">
                    {{ user.fullName }} - {{ user.userName }}
                </li>
            </ul>
        </p>
    </div>
</template>

<script>
import ProductList from "./products/List.vue";
export default {
    name: 'app',
    components: {
        ProductList: ProductList
    },
    data () {
        return {
            time: new Date().toString(),
            users: []
        }
    },
    mounted () {
        fetch('/api/users')
            .then(response => {
                return response.json()
            })
            .then(data => {
                this.users = data
            })
    }
}
</script>