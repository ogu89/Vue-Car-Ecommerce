<script setup>
import { defineProps } from "vue";

const props = defineProps({
  item: Object
})

</script>

<template>
  <div class="card m-2" style="width: 18rem">
    <div class="card-body">
      <img :src="props.item.imgUrl" class="card-img-top" alt="..." />
      <h5 class="card-title pt-2">{{ props.item.name }}</h5>
      <p class="card-text">Category: {{ props.item.category }}</p>
      <p class="card-text">Price: {{ props.item.price }}</p>
      <p class="card-text">Date:{{ props.item.date }}</p>
    </div>
  </div>
</template>

<style scoped>
</style>
