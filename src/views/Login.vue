<template>
  <div>
    <h3>Formulario</h3>
    <form @submit.prevent="validarForm">
      <label for="correo">Correo: </label>
      <input v-model="email" id="correo" type="text" required />
      <label for="contraseña">Contraseña: </label>
      <input
        v-model="password"
        placeholder="introduce tu contraseña"
        id="contraseña"
        type="password"
        required
      />
      <button type="submit">Validar</button>
    </form>
    
  </div>
</template>
<script>
import Firebase from "firebase";
export default {
  // datos para login: usuario1@gmail.com || 123456
  data: () => ({
    email: "",
    password: "",
  }),
   // Redireccionar a home cuando se valide formulario
  methods: {
    validarForm() {
      Firebase.auth()
        .signInWithEmailAndPassword(this.email, this.password)
        .then((response) => {
          this.$router.push("Home");
        })
        .catch((response) => {
          console.error(response);
        });
    },
  },
//   logout() {
//     Firebase.auth()
//       .signOut()
//       .then((accept) => {
//         this.$router.push("Login");
//       });
//   },
};
</script>
