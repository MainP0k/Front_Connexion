<template>
  <div class="auth-container">
    <h1>Connexion</h1>
    <form v-if="!verificationCode" @submit.prevent="sendCode">
      <div class="form-group">
        <label for="username">Nom d'utilisateur :</label>
        <input type="text" id="username" v-model="username" required />
      </div>
      <div class="form-group">
        <label for="password">Mot de passe :</label>
        <input type="password" id="password" v-model="password" required />
      </div>
      <div class="form-group">
        <button type="submit">Se connecter</button>
      </div>
    </form>
    <form v-else @submit.prevent="verifyCode">
      <div class="form-group">
        <label for="code">Code de vérification :</label>
        <input type="text" id="code" v-model="verificationCodeInput" required />
      </div>
      <div class="form-group">
        <button type="submit">Vérifier le code</button>
      </div>
    </form>
    <div v-if="errorMessage" class="error-message">{{ errorMessage }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: "",
      password: "",
      verificationCode: "",
      verificationCodeInput: "",
      errorMessage: "",
    };
  },
  methods: {
    sendCode() {
      // Envoi du code de vérification par e-mail
      // Remplacer "email@example.com" par l'e-mail de l'utilisateur
      const email = "email@example.com";
      const code = Math.floor(Math.random() * 1000000).toString();
      console.log(`Code de vérification envoyé à ${email}: ${code}`);
      // Simuler l'envoi du code
      this.verificationCode = code;
    },
    verifyCode() {
      // Vérification du code de vérification
      if (this.verificationCodeInput === this.verificationCode) {
        // Redirection vers la page d'accueil ou autre page
        console.log("Authentification réussie!");
      } else {
        this.errorMessage = "Code de vérification invalide";
      }
    },
  },
};
</script>

<style scoped>
.auth-container {
  max-width: 400px;
  margin: 0 auto;
  text-align: center;
  padding-top: 50px;
}

h1 {
  font-size: 32px;
  margin-bottom: 30px;
}

form {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form-group {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-size: 18px;
  margin-bottom: 10px;
}

input[type="text"],
input[type="password"] {
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 5px;
  width: 100%;
  max-width: 300px;
}

button[type="submit"] {
  padding: 10px 20px;
  font-size: 18px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.error-message {
  color: red;
  margin-top: 20px;
}
</style>