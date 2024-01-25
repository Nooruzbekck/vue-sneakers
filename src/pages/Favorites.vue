<script setup>
import axios from 'axios'
import { onMounted, ref } from 'vue'
import CardList from '@/components/CardList.vue'

const favorites = ref([])

onMounted(async () => {
  try {
    const { data } = await axios.get(
      'https://d46c3352c4399ef3.mokky.dev/favorites?_relations=items'
    )
    favorites.value = data.map((item) => item.item)
  } catch (error) {
    console.log(error)
  }
})
</script>

<template>
  <h2 class="text-3xl font-bold mb-8">Мои закладки</h2>
  <CardList :items="favorites" is-favorites />
</template>
