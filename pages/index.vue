<script setup lang="ts">
const theme = useState('theme')

const colors = computed(() => {
  if (theme.value) {
    return JSON.parse(theme.value).colors
  } else {
    return {}
  }
})

const uniqueColors = computed(() => {
  const unique = new Set<string>()
  for (const key in colors.value) {
    unique.add(colors.value[key])
  }
  return Array.from(unique).filter(color => color !== null)
})
</script>

<template>
  <div>
    <nav>
      <NuxtLink to="/">Home</NuxtLink>
      <NuxtLink to="/data">Data</NuxtLink>
    </nav>
    <ul class="color-grid">
      <li v-for="(color, index) in uniqueColors" :index="`color-${index}`">
        <div class="color-swatch" :style="`background-color: ${color}`"></div>
        <div>{{ color }}</div>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.color-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  row-gap: 1rem;
}

.color-swatch {
  width: 250px;
  height: 250px;
}
</style>
