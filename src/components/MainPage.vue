<template>
  <div class="container">
    <div class="card">
      <h1 class="title">
        Digitalisasi Boring Log Prototype
      </h1>

      <p class="subtitle">
        Upload foto form boring log untuk diproses menggunakan OCR dan 
        menghasilkan laporan PDF terstruktur.
      </p>

      <div class="upload-section">
        <input 
          type="file" 
          accept="image/*" 
          @change="handleFileChange"
          ref="fileInput"
          hidden
        />

        <button class="upload-btn" @click="triggerFileInput">
          Upload Gambar
        </button>

        <p v-if="fileName" class="file-name">
          File dipilih: {{ fileName }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MainPage",
  data() {
    return {
      fileName: null,
      selectedFile: null
    };
  },
  methods: {
    triggerFileInput() {
      this.$refs.fileInput.click();
    },
    handleFileChange(event) {
      const file = event.target.files[0];
      if (file) {
        this.selectedFile = file;
        this.fileName = file.name;
        console.log("File selected:", file);
      }
    }
  }
};
</script>

<style scoped>
.container {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #f4f6f8;
}

.card {
  background: white;
  padding: 40px;
  border-radius: 12px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.05);
  width: 420px;
  text-align: center;
}

.title {
  font-size: 22px;
  margin-bottom: 10px;
  font-weight: 600;
}

.subtitle {
  font-size: 14px;
  color: #666;
  margin-bottom: 30px;
}

.upload-section {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.upload-btn {
  padding: 12px 24px;
  background-color: #2c3e50;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 14px;
  transition: 0.2s ease;
}

.upload-btn:hover {
  background-color: #1a252f;
}

.file-name {
  margin-top: 15px;
  font-size: 13px;
  color: #333;
}
</style>
