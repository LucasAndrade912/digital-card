<script setup>
import { reactive, ref, watch } from 'vue'

import CardForm from './components/CardForm.vue'
import DigitalCard from './components/DigitalCard.vue'

const image = ref(null)
const imageName = ref('')

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
      :imageName="imageName"
      @change:image="
        (file) => {
          image = file
          imageName = file.name
        }
      "
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
  padding: 0 4rem;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  gap: 80px;
  align-items: center;
}
</style>
