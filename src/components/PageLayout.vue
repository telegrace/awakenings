<script setup lang="ts">
const handleNextButtonClick = () => {
  console.log('Show cards')
}

const props = defineProps({
  subtitle: String
})
</script>

<template>
  <div class="container">
    <header>
      <h1>Awakenings: craft stories, build bonds</h1>
      <h2>{{ props.subtitle }}</h2>
    </header>
    <main>
      <slot name="content" />
    </main>
  </div>
</template>
