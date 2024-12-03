<template>
  <div
    class="container-fluid min-vh-100 d-flex align-items-center justify-content-center bg-white"
  >
    <div class="col-12 col-md-3 p-0 bg-gradient rounded-3 max-width-300">
      <div class="p-4 bg-white rounded-3 bg-pattern">
        <h1 class="h5 font-sans fw-semibold text-dark text-center">
          Scan QR Code
        </h1>
        <p class="text-muted text-center">
          Please scan the QR code displayed below with your camera to proceed:
        </p>

        <!-- QR Code Image Placeholder -->
        <div
          class="qr-code-placeholder d-flex align-items-center justify-content-center mb-3 mx-auto"
        >
          <img :src="qrCodeImage" alt="QR Code" class="qr-image" />
        </div>

        <p class="small text-muted text-center">
          Ensure the QR code is fully visible within the frame of your camera.
        </p>

        <!-- Logo Placeholder -->
        <div class="text-center mb-3">
          <img
            :src="logoSrc"
            alt="Logo"
            :style="{ width: logoSize + 'px', height: 'auto' }"
          />
        </div>

        <!-- Button to Regenerate QR Code -->
        <div class="text-center">
          <button @click="generateNewQRCode" class="btn btn-primary w-100 mt-3">
            Generate New QR Code
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'QRCodeDisplay',
  props: {
    logoSize: {
      type: Number,
      default: 80, // Taille du logo réduite
    },
    logoSrc: {
      type: String,
      default: 'https://cdn.worldvectorlogo.com/logos/blue-1.svg', // URL par défaut du logo
    },
  },
  data() {
    return {
      qrCodeImage:
        'https://api.qrserver.com/v1/create-qr-code/?size=250x250&data=DemoQRCode',
    };
  },
  methods: {
    generateNewQRCode() {
      this.qrCodeImage = `https://api.qrserver.com/v1/create-qr-code/?size=250x250&data=DemoQRCode_${Math.random()}`;
    },
  },
  mounted() {
    // Changement du QR code toutes les 30 secondes
    this.generateNewQRCode(); // Génération initiale
    setInterval(this.generateNewQRCode, 30000); // Changement automatique toutes les 30 secondes
  },
};
</script>

<style scoped>
.bg-pattern {
  background-color: white; /* Fond blanc simple */
  border: 2px solid var(--bs-primary); /* Même couleur que le bouton */
  padding: 6rem; /* Réduction du padding */
}

.qr-code-placeholder {
  width: 250px;
  height: 250px;
  border: 0;
  border-radius: 0;
  overflow: hidden;
  position: relative;
  margin: 0 auto;
}

.qr-image {
  object-fit: cover;
  width: 100%;
  height: 100%;
}

.logo-image {
  width: 80px; /* Taille du logo ajustée */
  height: auto; /* Conserver le ratio */
}
</style>
