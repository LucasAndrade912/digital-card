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
    <div id="logo">
      <img :src="image ?? '/default-image.jpg'" alt="logo" />
    </div>

    <div id="info">
      <h2>{{ cardData.title || 'Título' }}</h2>
      <h3>{{ cardData.subtitle || 'Subtítulo' }}</h3>

      <ul>
        <li><span>Telefone</span>: {{ cardData.phone }}</li>
        <li><span>Endereço</span>: {{ cardData.address }}</li>
        <li><span>Email</span>: {{ cardData.email }}</li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
#digital-card {
  position: relative;
  display: grid;
  align-items: center;
  grid-template-columns: 45% 55%;
  padding: 40px;
  border-radius: 14px;
  width: 732px;
  background-color: #e6e5e5;
  color: #000;
}

#digital-card img {
  position: relative;
  z-index: 10;
  width: 224px;
  height: 224px;
  border-radius: 50%;
}

#digital-card #logo::after {
  content: '';
  width: 28%;
  height: 100%;
  position: absolute;
  display: block;
  top: 0;
  left: 0;
  background-color: #883bf9;
  border-top-left-radius: 14px;
  border-bottom-left-radius: 14px;
}

#digital-card #info {
  text-align: left;
}

#digital-card #info h2,
h3 {
  font-family: 'Kode Mono', monospace;
  font-weight: 700;
  margin: 0;
}

#digital-card #info h2 {
  font-size: 3rem;
  margin-bottom: 0.875rem;
  position: relative;
}

#digital-card #info h3 {
  font-size: 1.5rem;
  background-color: #46d934;
  display: inline-block;
  padding: 0.25rem;
  border-radius: 0.25rem;
  margin-bottom: 1.25rem;
}

#digital-card #info ul {
  list-style: none;
  font-weight: 500;
  font-family: 'Poppins', sans-serif;
  padding: 0;
}

#digital-card #info ul li {
  position: relative;
  margin-bottom: 4px;
  display: flex;
}

#digital-card #info ul li span {
  display: block;
  position: relative;
  font-weight: 600;
}

#digital-card #info ul li span::after {
  background-color: #46d934;
  position: absolute;
  bottom: 0;
  left: 0;
  content: '';
  width: 40px;
  height: 3px;
}
</style>
