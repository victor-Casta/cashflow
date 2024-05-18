<template>
    <Layout>
        <template #header>
            <Header />
        </template>
    </Layout>
</template>

<script>
    import Layout from './Layout.vue';
    import Header from './Header.vue';

    export default {
        components: {
            Layout,
            Header
        }
    }
</script>