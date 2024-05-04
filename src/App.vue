<template>
  <div class="anggita">
    <h1>Anggita wahyudini putri </h1>

    <p>Email:</p>
    <!-- Input email -->
    <input type="text" v-model="email" :style="{ 'background-color': buttonBackgroundColor }" @blur="validateEmail">
    <p class="input-info">Panjang maksimum teks: 10 karakter </p>
    <p v-if="isRedEmail" class="red-text">Email tidak valid!</p>
    <p>Nilai input teks: <span :class="{ 'red-text': isRedEmail }">{{ email }}</span></p>
    <p>Password:</p>
    <!-- Input password -->
    <input type="password" v-model="password" :style="{ 'background-color': buttonBackgroundColor }" @blur="validatePassword">
    <p class="input-info">Panjang maksimum teks: 10 karakter </p>
    <p v-if="isRedPassword" class="red-text">Password harus memiliki setidaknya 6 karakter dan minimal satu angka!</p>
    <p>Nilai input teks: <span :class="{ 'red-text': isRedPassword }">{{ password }}</span></p>
    <!-- Tambahkan input untuk tanggal lahir  -->
    <p>Tanggal Lahir:</p>
    <input type="date" v-model="tanggalLahir">

    <!-- Tombol untuk mengubah warna latar belakang -->
    <button :style="{ 'background-color': buttonBackgroundColor }" @click="changeColor">Ubah Warna Latar Belakang Tombol</button>
    <br>
    <!-- V-calendar -->
    <v-calendar v-model="selectedDate"></v-calendar>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      isRedEmail: false,
      isRedPassword: false,
      buttonBackgroundColor: '#E6B3B3',
      selectedDate: null,
      tanggalLahir: '',
    }
  },
  methods: {
    validateEmail() {
      // Regular expression for email validation
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      this.isRedEmail = !emailRegex.test(this.email);
    },
    validatePassword() {
      // Password validation logic (example: minimum length of 6 characters and at least one number)
      this.isRedPassword = this.password.length < 6 || !/\d/.test(this.password);
    },
    changeColor() {
      this.buttonBackgroundColor = 'green';
    },
  }
}
</script>

<style scoped>
/* CSS Styles */
.anggita {
  background: linear-gradient(135deg, #ffbbcb, #ff7eb9, #ff389f, #f81281, #c70062); /* Pink gradient palette */
  background-repeat: no-repeat;
  background-size: cover;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

h1 {
  color: #333;
  height: 10%;
}

p {
  color: #555;
  margin-bottom: 5px;
  text-align: left;
}

input[type="text"], input[type="date"], input[type="password"] {
  width: 20%;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 16px;
  box-sizing: border-box;
  z-index: 2; 
}

.input-info {
  font-size: 14px;
  color: #999;
  margin-top: -10px;
  margin-bottom: 10px;
}

span {
  font-size: 18px;
  color: #333;
  font-weight: bold;
}

.red-text {
  color: red;
}

button {
  padding: 5px 5px;
  background-color: #3498db;
  color: #fff;
  border: none;
  border-radius: 2px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #2980b9;
}
</style>
