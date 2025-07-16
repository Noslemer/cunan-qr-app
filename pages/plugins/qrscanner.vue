<template>
  <div>
    <h1>QR Code Scanner</h1>

    <qrcode-stream @decode="onDecode" @init="onInit">
      <div v-if="error" class="error">
        Camera access denied or not available.
      </div>
    </qrcode-stream>

    <div v-if="decodedContent">
      <h2>Scanned QR Code:</h2>
      <p>{{ decodedContent }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      decodedContent: '',
      error: false,
    }
  },
  methods: {
    onDecode(content) {
      this.decodedContent = content
    },
    onInit(promise) {
      promise.catch(() => {
        this.error = true
      })
    }
  }
}
</script>

<style scoped>
.error {
  color: red;
  font-weight: bold;
}
</style>
