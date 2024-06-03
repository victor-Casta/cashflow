<template>
    <Layout>
        <template #header >
            <Header />
        </template>
        <template #resume >
            <Resume
                :total-label="'Ahorro total'"
                :label="label"
                :total-amount="totalAmount"
                :amount="amount"
            >
                <template #graphic>
                    <Graphic :amounts="amounts" @select="select"/>
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
            movements: []
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
                const lastMovements = lastDays.slice(0, i + 1)
                return lastMovements.reduce((acc, movement) => {
                    return acc + movement
                }, 0)
            })
        },
        totalAmount() {
            return this.movements.reduce((acc, movement) => {
                return acc + movement.amount
            }, 0)
        }
    },
    mounted() {
        const movements = JSON.parse(localStorage.getItem('movements'))
        if (Array.isArray(movements)) {
            this.movements = movements.map(movement => {
            return {
                ...movement,
                time: new Date(movement.time)
            }
        })
        }
    },
    methods: {
        create(movement) {
            this.movements.push(movement)
            this.save()
        },
        remove(id) {
           const index = this.movements.findIndex(movement => movement.id === id)
           this.movements.splice(index, 1)
           this.save()
        },
        save() {
            localStorage.setItem('movements', JSON.stringify(this.movements))
        },
        select(amount) {
            this.amount = amount
        }
    }
};
</script>
