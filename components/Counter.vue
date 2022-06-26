<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps({
  count: {
    default: 0,
  },
})

const count = ref(props.count)
</script>

<template>
  <button
  bg="green-300"
  px="4"
  py="2"
  text="black"
  border="2 green-600 rounded"
   @click="count++" type="button">Count is: {{ count }}</button>
</template>
