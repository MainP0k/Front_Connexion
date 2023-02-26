<template>
  <div class="auth-container">
    <h1>Connexion</h1>
    <form @submit.prevent="login">
      <div class="form-group">
        <label for="username">Nom d'utilisateur :</label>
        <input type="text" id="username" v-model="username" required>
      </div>
      <div class="form-group">
        <label for="password">Mot de passe :</label>
        <input type="password" id="password" v-model="password" required>
      </div>
      <div class="form-group">
        <button type="submit">Se connecter</button>
      </div>
    </form>
    <div v-if="errorMessage" class="error-message">{{ errorMessage }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: '',
      errorMessage: ''
    };
  },
  methods: {
    login() {
      // Vérification des identifiants
      if (this.username === 'mon_nom_utilisateur' && this.password === 'mon_mot_de_passe') {
        // Redirection vers la page d'accueil ou autre page
        console.log('Authentification réussie!');
      } else {
        this.errorMessage = 'Nom d\'utilisateur ou mot de passe invalide';
      }
    }
  }
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
  font-size: 16px;
  margin-top: 20px;
}
</style>
