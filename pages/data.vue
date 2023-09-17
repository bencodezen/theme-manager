<script setup lang="ts">
const themeData = useState('theme', () => '')

const theme = computed(() => {
  if (themeData.value) {
    return JSON.parse(themeData.value)
  } else {
    return {}
  }
})

watch(theme, newTheme => {
  useState('theme', () => newTheme)
})
</script>

<template>
  <div>
    <nav>
      <NuxtLink to="/">Home</NuxtLink>
      <NuxtLink to="/data">Data</NuxtLink>
    </nav>
    <label for="theme-data">Theme Data</label>
    <textarea v-model="themeData" name="theme-data" id="theme-data"></textarea>
  </div>
</template>

<style scoped>
div {
  display: flex;
  flex-direction: column;
}

label {
  margin-bottom: 1rem;
}

textarea {
  width: 100%;
  height: 80vh;
}
</style>
