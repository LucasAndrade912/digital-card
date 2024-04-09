<script setup>
defineProps({
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
</script>

<template>
  <form>
    <div class="input-field">
      <label for="logo">Imagem:</label>
      <input type="file" id="logo" @change="$emit('change:image', $event.target.files[0])" />
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

    <input type="submit" value="Export to PNG" />
  </form>
</template>
