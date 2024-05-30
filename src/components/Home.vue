<template>
    <Layout>
        <template #header >
            <Header />
        </template>
        <template #resume >
            <Resume
                :total-label="'Ahorro total'"
                :label="label"
                :total-amount="1000000"
                :amount="amount"
            >
                <template #graphic>
                    graphic
                </template>
                <template #action>
                    <Action />
                </template>
            </Resume>
        </template>
        <template #movements>
            <Movements
            :movements="movements"
            />
        </template>
    </Layout>
</template>

<script>
    import Layout from './Layout.vue';
    import Header from './Header.vue';
    import Resume from './Resume/index.vue';
    import Movements from './Movements/index.vue';
    import Action from './Action.vue';

    export default {
        components: {
            Layout,
            Header,
            Resume,
            Movements,
            Action
        },
        data() {
            return {
                label: null,
                amount: null,
                movements: [
                {
                    id: 0,
                    title: 'House',
                    description: 'pay',
                    amount: 1000000
                },
                {
                    id: 1,
                    title: 'Car',
                    description: 'pay',
                    amount: 9000000
                },
                {
                    id: 2,
                    title: 'Food',
                    description: 'pay',
                    amount: 400000
                },
                {
                    id: 3,
                    title: 'Clothes',
                    description: 'pay',
                    amount: 189000
                },
                {
                    id: 4,
                    title: 'Tecnology',
                    description: 'pay',
                    amount: 40000
                },
                {
                    id: 5,
                    title: 'Inversion',
                    description: 'pay',
                    amount: 4000000
                },
                ]
            }
        }
    }
</script>