<template>        
    <div>
        <b-nav tabs>
            <b-nav-item active>Active</b-nav-item>
            <b-nav-item>Link</b-nav-item>
            <b-nav-item>Another Link</b-nav-item>
            <b-nav-item disabled>Disabled</b-nav-item>
        </b-nav>
        <b-nav pills>
            <b-nav-item active>Active</b-nav-item>
            <b-nav-item>Link</b-nav-item>
            <b-nav-item>Another Link</b-nav-item>
            <b-nav-item disabled>Disabled</b-nav-item>
        </b-nav>
        <b-navbar toggleable type="light" variant="light">
            <b-navbar-toggle target="nav_text_collapse" />

            <b-navbar-brand>BootstrapVue</b-navbar-brand>

            <b-collapse is-nav id="nav_text_collapse">
            <b-navbar-nav>
                <b-nav-text>Navbar text</b-nav-text>
            </b-navbar-nav>
            </b-collapse>
        </b-navbar>
        <b-navbar toggleable="lg" type="dark" variant="info">
            <b-navbar-brand href="#">NavBar</b-navbar-brand>

            <b-navbar-toggle target="nav_collapse" />

            <b-collapse is-nav id="nav_collapse">
            <b-navbar-nav>
                <b-nav-item href="#">Link</b-nav-item>
                <b-nav-item href="#" disabled>Disabled</b-nav-item>
            </b-navbar-nav>

            <!-- Right aligned nav items -->
            <b-navbar-nav class="ml-auto">
                <b-nav-form>
                <b-form-input size="sm" class="mr-sm-2" type="text" placeholder="Search" />
                <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
                </b-nav-form>

                <b-nav-item-dropdown text="Lang" right>
                <b-dropdown-item href="#">EN</b-dropdown-item>
                <b-dropdown-item href="#">ES</b-dropdown-item>
                <b-dropdown-item href="#">RU</b-dropdown-item>
                <b-dropdown-item href="#">FA</b-dropdown-item>
                </b-nav-item-dropdown>

                <b-nav-item-dropdown right>
                <!-- Using button-content slot -->
                <template slot="button-content"><em>User</em></template>
                <b-dropdown-item href="#">Profile</b-dropdown-item>
                <b-dropdown-item href="#">Signout</b-dropdown-item>
                </b-nav-item-dropdown>
            </b-navbar-nav>
            </b-collapse>
        </b-navbar>
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
    </div>
</template>

<script>
export default {
    name: 'app',
    data () {
        return {
            time: new Date().toString()
        }
    }
}
</script>