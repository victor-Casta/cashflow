<template>
    <Layout>
        <template #header >
            <Header />
        </template>
        <template #resume >
            <Resume />
        </template>
        <template #movements>
            <Movements />
        </template>
    </Layout>
</template>

<script>
    import Layout from './Layout.vue';
    import Header from './Header.vue';
    import Resume from './Resume/index.vue';
    import Movements from './Movements.vue';

    export default {
        components: {
            Layout,
            Header,
            Resume,
            Movements
        }
    }
</script>