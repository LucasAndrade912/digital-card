<script setup>
import { reactive, ref, watch } from 'vue'

import CardForm from './components/CardForm.vue'
import DigitalCard from './components/DigitalCard.vue'

const image = ref(null)

const cardData = reactive({
  title: '',
  subtitle: '',
  phone: '',
  address: '',
  email: ''
})

watch(image, () => {
  if (image.value instanceof File) image.value = URL.createObjectURL(image.value)
})
</script>

<template>
  <main>
    <CardForm
      @change:image="(file) => (image = file)"
      v-model:title="cardData.title"
      v-model:subtitle="cardData.subtitle"
      v-model:phone="cardData.phone"
      v-model:address="cardData.address"
      v-model:email="cardData.email"
    />
    <DigitalCard :cardData="cardData" :image="image" />
  </main>
</template>

<style scoped>
main {
  width: 100%;
  display: flex;
  justify-content: space-between;
}
</style>
