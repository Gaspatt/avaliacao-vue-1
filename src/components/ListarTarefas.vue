<script setup>
defineProps({
  realizadas: {
    type: Boolean,
    default: false
  },
  tarefas: [
    { id: 1, descricao: 'Fazer avaliação 1', feita: true },
    { id: 2, descricao: 'Fazer avaliação 2', feita: false },
    { id: 3, descricao: 'Fazer avaliação 3', feita: false },
    { id: 4, descricao: 'Fazer avaliação 4', feita: false },
    { id: 5, descricao: 'Fazer avaliação 5', feita: false }
  ]
})
</script>

<template>
  <section
    v-for="tarefa in tarefas"
    :key="tarefa.id"
    :class="{ feita: tarefa.feita }"
    @click="$emit('click', tarefa.id)"
  >
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
