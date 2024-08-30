<script setup>

const tarefas = defineProps({
    realizadas: {
        type: Boolean,
        default: false
    }
})

</script>

<template>
    <section v-for="tarefa in tarefas" :key="tarefa.id" :class="{ 'feita': tarefa.feita }"
        @click="$emit('click', adicionarTarefa.id)">
        <Transition name="fade">
            <p v-if="realizadas ? tarefa.feita : !tarefa.feita">{{ tarefa.descricao }}</p>
        </Transition>
    </section>
</template>

<style scoped>
.feita {
    text-decoration: line-through;
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 2s ease-in-out;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}
</style>