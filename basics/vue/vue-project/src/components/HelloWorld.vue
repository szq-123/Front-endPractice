<script setup>
// specify variables come from parental components.
// variables defined in props are read-only.
const props = defineProps({
  msg: {
    type: String,
    required: true
  },
  msg1: {
    type: String,
    default: "Fabulous!",
  },
  num: {
    type: Number,
    default: 1,
  }
})

// define events to deliver value to parents.
const emit = defineEmits(
    ['hello-world-praise', 'update:num']
)

const deliverPraise = () => {
  console.log('deliverPraise')
  emit('hello-world-praise', 'You are the Number One!')

  // update num sent by parent.
  emit('update:num', 100)
}
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }} {{ msg1 }}</h1>
    <h3>
      You’ve successfully created a project with
      <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
      <button @click="deliverPraise">Praise yourself!</button>
    </h3>
    {{num}}
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
