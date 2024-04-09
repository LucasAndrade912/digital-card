<script setup>
defineProps({
  cardData: {
    image: {
      required: true,
      type: String
    },
    title: {
      required: true,
      type: String
    },
    subtitle: {
      required: true,
      type: String
    },
    phone: {
      required: true,
      type: String
    },
    address: {
      required: true,
      type: String
    },
    email: {
      required: true,
      type: String
    }
  },
  image: {
    required: true,
    type: [String, null]
  }
})
</script>

<template>
  <div id="digital-card">
    <img :src="image ?? '/default-image.jpg'" alt="logo" />

    <div id="info">
      <h2>{{ cardData.title || 'Título' }}</h2>
      <h3>{{ cardData.subtitle || 'Subtítulo' }}</h3>

      <ul>
        <li>Telefone: {{ cardData.phone }}</li>
        <li>Endereço: {{ cardData.address }}</li>
        <li>Email: {{ cardData.email }}</li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
#digital-card {
  display: flex;
  justify-content: space-between;
  padding: 40px;
  border-radius: 14px;
  width: 764px;
  background-color: #fff;
  color: #000;
}

#digital-card img {
  width: 224px;
  height: 224px;
  border-radius: 50%;
}
</style>
