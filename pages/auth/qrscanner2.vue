<template>
  <div>
    <div ref="reader" id="reader" style="width: 300px;"></div>
    <p v-if="scannedResult">Scanned: {{ scannedResult }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      scannedResult: null,
      html5QrCode: null,
    };
  },
  mounted() {
    if (process.client) {
      import("html5-qrcode").then(({ Html5Qrcode }) => {
        this.html5QrCode = new Html5Qrcode("reader");

        const config = { fps: 10, qrbox: 250 };

        this.html5QrCode.start(
          { facingMode: "environment" },
          config,
          (decodedText, decodedResult) => {
            this.scannedResult = decodedText;
            this.html5QrCode.stop(); // Stop after first scan
          },
          (errorMessage) => {
            // Optional: console.log(errorMessage);
          }
        );
      });
    }
  },
  beforeDestroy() {
    if (this.html5QrCode && this.html5QrCode.stop) {
      this.html5QrCode.stop().then(() => {
        this.html5QrCode.clear();
      });
    }
  },
};
</script>
