<template>
    <navbar-vue />
    <router-view></router-view>
</template>

<script>
import NavbarVue from './components/Navbar.vue'
export default {
    name: 'App',
    components: {
        NavbarVue,
    },
}
</script>
