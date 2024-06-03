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
                    <Graphic :amounts="amounts" />
                </template>
                <template #action>
                    <Action @create="create" />
                </template>
            </Resume>
        </template>
        <template #movements>
            <Movements
            :movements="movements"
            @remove="remove"
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
import Graphic from './Resume/Graphic.vue';

export default {
    components: {
        Layout,
        Header,
        Resume,
        Movements,
        Action,
        Graphic
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
                    amount: 300000,
                    time: new Date("05-22-2024")
                },
                {
                    id: 1,
                    title: 'Car',
                    description: 'pay',
                    amount: 100000,
                    time: new Date("05-22-2024")
                },
                {
                    id: 2,
                    title: 'Food',
                    description: 'pay',
                    amount: -50000,
                    time: new Date("05-12-2024")
                },
                {
                    id: 3,
                    title: 'Clothes',
                    description: 'pay',
                    amount: -50000,
                    time: new Date("05-12-2024")
                },
                {
                    id: 4,
                    title: 'Tecnology',
                    description: 'pay',
                    amount: 200000,
                    time: new Date("06-01-2024")
                },
                {
                    id: 5,
                    title: 'Inversion',
                    description: 'pay',
                    amount: 100000,
                    time: new Date("06-01-2024")
                }
            ]
        };
    },
    computed: {
        amounts() {
            const lastDays = this.movements.filter(movement => {
                const today = new Date();
                const oldDay = today.setDate(today.getDate() - 30);
                return movement.time > oldDay
            }).map(movement => movement.amount)
            return lastDays.map((m, i) => {
                const lastMovements = lastDays.slice(0, i)
                return lastMovements.reduce((acc, movement) => {
                    return acc + movement
                }, 0)
            })
        }
    },
    methods: {
        create(movement) {
            this.movements.push(movement)
        },
        remove(id) {
           const index = this.movements.findIndex(movement => movement.id === id)
           this.movements.splice(index, 1)
        }
    }
};
</script>
