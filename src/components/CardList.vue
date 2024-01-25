<script setup>
import Card from './Card.vue'
defineProps({
  items: Array,
  isFavorites: Boolean
})

const emit = defineEmits(['addToFavorite', 'addToCart'])
</script>

<template>
  <div v-auto-animate class="grid grid-cols-3 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :image-url="item.imageUrl"
      :title="item.title"
      :price="item.price"
      :id="item.id"
      :onClickFavorite="isFavorites ? null : () => emit('addToFavorite', item)"
      :isFavorite="item.isFavorite"
      :onClickAdd="isFavorites ? null : () => emit('addToCart', item)"
      :is-added="item.isAdded"
    />
  </div>
</template>
