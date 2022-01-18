<template>
    <header-vue />
    <promos-vue />
    <incentives-vue />
</template>

<script>
import HeaderVue from '../components/Header.vue';
import IncentivesVue from '../components/Incentives.vue';
import PromosVue from '../components/Promos.vue';
export default {
    name: 'Home',
    components: {
        HeaderVue,
        IncentivesVue,
        PromosVue,
    },
};
</script>
