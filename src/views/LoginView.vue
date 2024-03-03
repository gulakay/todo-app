<template>
  <div class="login-container">
    <input
      v-model="loginUser"
      type="text"
      name="username"
      placeholder="Username"
    />
    <br />
    <input
      v-model="loginPassword"
      type="password"
      name="password"
      placeholder="Password"
    />
    <br />
    <button @click="loginFunc">Login</button>
    <span v-if="isError">{{ errorMess }}</span>
  </div>
</template>

<script>
import { ref } from "vue";
import { useRouter } from "vue-router";
export default {
  name: "LoginView",
  components: {},
  setup() {
    const loginUser = ref();
    const loginPassword = ref();

    const router = useRouter();
    const isError = ref(false);
    const errorMess = ref();

    const loginFunc = () => {
      const user = "Gül";
      const pass = "furkan";

      if (user === loginUser.value && pass === loginPassword.value) {
        router.push({ name: "AddTodos" });
      } else if (user === loginUser.value && pass !== loginPassword.value) {
        isError.value = true;
        errorMess.value = "Parola Hatalı!";
      } else if (user !== loginUser.value && pass === loginPassword.value) {
        isError.value = true;
        errorMess.value = "Kullanıcı Adı Hatalı!";
      } else if (user !== loginUser.value && pass !== loginPassword.value) {
        isError.value = true;
        errorMess.value = "Kullanıcı Bulunamadı!";
      }
    };

    return { loginUser, loginPassword, loginFunc, isError, errorMess };
  },
};
</script>
<style>
input {
  width: 300px;
  margin: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 8px;
  font-size: 16px;
  outline: none;
}
input:focus {
  border-color: #5d1b7d;
}
button {
  padding: 10px 20px;
  margin: 20px;
  background-color: #686868;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}

button:hover {
  background-color: #5d1b7d; /* Butonun rengini değiştirir */
}
</style>
