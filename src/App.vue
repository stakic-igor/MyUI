<script setup lang="ts">
import UiButton from './components/ui/UiButton.vue'

const variants = ['primary', 'secondary', 'outline', 'danger'] as const
const sizes = ['sm', 'md', 'lg'] as const
</script>

<template>
  <main class="demo">
    <section v-for="variant in variants" :key="variant" class="row">
      <h3>{{ variant }}</h3>
      <UiButton v-for="size in sizes" :key="size" :variant="variant" :size="size">
        {{ variant }} {{ size }}
      </UiButton>
      <UiButton :variant="variant" disabled>disabled</UiButton>
    </section>

    <section class="row">
      <h3>type</h3>
      <form @submit.prevent>
        <UiButton type="submit">Submit</UiButton>
        <UiButton type="reset" variant="outline">Reset</UiButton>
      </form>
    </section>
  </main>
</template>

<style scoped>
.demo {
  display: grid;
  gap: 24px;
  padding: 24px;
}
.row,
.row form {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 12px;
}
.row h3 {
  width: 100px;
  margin: 0;
  text-transform: capitalize;
}
</style>
