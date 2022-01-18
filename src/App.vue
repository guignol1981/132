<template>
    <navbar-vue />
    <router-view></router-view>
    <footer-vue />
</template>

<script>
import FooterVue from './components/Footer.vue';
import NavbarVue from './components/Navbar.vue';
export default {
    name: 'App',
    components: {
        NavbarVue,
        FooterVue,
    },
};
</script>
