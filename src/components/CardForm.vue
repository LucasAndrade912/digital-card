<script setup>
import domtoimage from 'dom-to-image'

defineProps({
  imageName: String,
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
})

defineEmits([
  'change:image',
  'update:title',
  'update:subtitle',
  'update:phone',
  'update:address',
  'update:email'
])

async function downloadCard(event) {
  event.preventDefault()

  const digitaCardRef = document.querySelector('#digital-card')
  const dataURL = await domtoimage.toJpeg(digitaCardRef, {
    bgcolor: 'transparent',
    style: { fontFamily: 'Poppins, sans-serif' }
  })
  const link = document.createElement('a')

  link.download = 'digital-card.jpg'
  link.href = dataURL
  link.click()
}
</script>

<template>
  <form @submit="downloadCard($event)">
    <div class="input-field">
      <label for="logo">Imagem:</label>
      <label id="custom-input-file">
        <span v-if="imageName">{{ imageName }}</span>

        <div v-else>
          <img src="../assets/upload.svg" alt="Upload file icon" />
          <span>Selecione uma imagem</span>
        </div>

        <input
          type="file"
          id="logo"
          accept=".jpg, .jpeg, .png"
          @change="$emit('change:image', $event.target.files[0])"
        />
      </label>
    </div>

    <div class="input-field">
      <label for="card-title">Título:</label>
      <input
        type="text"
        id="card-title"
        placeholder="Informe o tiulo do cartão"
        :value="title"
        @input="$emit('update:title', $event.target.value)"
      />
    </div>

    <div class="input-field">
      <label for="card-subtitle">Sub-título:</label>
      <input
        type="text"
        id="card-subtitle"
        placeholder="Informe o tiulo do cartão"
        :value="subtitle"
        @input="$emit('update:subtitle', $event.target.value)"
      />
    </div>

    <div class="input-field">
      <label for="phone">Telefone:</label>
      <input
        type="tel"
        id="phone"
        placeholder="(xx) xxxx-xxxx..."
        :value="phone"
        @input="$emit('update:phone', $event.target.value)"
      />
    </div>

    <div class="input-field">
      <label for="address">Endereço:</label>
      <input
        type="text"
        id="address"
        placeholder="Rua. Exemplo 000, Bairro"
        :value="address"
        @input="$emit('update:address', $event.target.value)"
      />
    </div>

    <div class="input-field">
      <label for="email">Email:</label>
      <input
        type="email"
        id="email"
        placeholder="dominio@exemplo.com"
        :value="email"
        @input="$emit('update:email', $event.target.value)"
      />
    </div>

    <button type="submit">Export to Image</button>
  </form>
</template>

<style scoped>
form {
  width: 100%;
  max-width: 39rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

form .input-field {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

form .input-field label {
  font-size: 1rem;
}

form .input-field input:not(input[type='file']),
#custom-input-file {
  background: none;
  border-radius: 0.25rem;
  border: 1px solid rgb(78, 78, 78);
  padding: 8px;
  color: #fff;
  font-size: 0.875rem;
}

form .input-field input[type='file'] {
  display: none;
}

form .input-field #custom-input-file {
  display: flex;
  align-items: center;
  justify-content: center;
  text-transform: uppercase;
  font-weight: 500;
  font-size: 1rem;
  padding: 0.875rem;
  cursor: pointer;
}

form .input-field #custom-input-file div {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

form button {
  border: none;
  background-color: #883bf9;
  padding: 1rem;
  font-size: 1rem;
  font-weight: 600;
  color: #fff;
  border-radius: 0.25rem;
  text-transform: uppercase;
  cursor: pointer;
  box-shadow: 0px 0.25rem 0.75rem rgba(255, 255, 255, 0.15);
  transition: background-color 200ms ease;
}

form button:hover {
  background-color: #7230d6;
}
</style>
