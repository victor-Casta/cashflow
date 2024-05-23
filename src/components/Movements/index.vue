<script setup>
    import { toRefs, defineProps } from "vue"

    const props = defineProps({
        movements: {
            type: Array,
            default: () => [],
        },
    })

    const { movements } = toRefs(props)

</script>

<template>
    <section class="Movements">
        <h2 class="title">Historial</h2>
        <div class="content">
            <div v-for="movement in movements" :key="movement.id">
                {{ movement.title }}
            </div>
        </div>
    </section>
</template>

<style scoped>
    .movements {
        max-height: 100%;
        padding: 0 8px;
        margin-bottom: 14px;
    }

    .title {
        margin: 8px 16px 24px 16px;
        color: #529fdf;
    }

    .content {
        max-height: 68vh;
        display: flex;
        flex-direction: column;
        gap: 8px;
        overflow-y: scroll;
        padding: 0 16px;
    }
</style>