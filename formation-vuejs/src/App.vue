<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
    
    <div>
      Hello {{ utilisateur.username }}, vous avez {{ utilisateur.age }} ans !
      <div>
        <input type="text" v-model="utilisateur.username" />
        <input type="number" v-model="utilisateur.age" />
      </div>

      <!-- v-on:eventName -->
      <!-- @eventName -->
      <button @click="demoClick()">Reset Username</button>
      <button @click="resetAge(10)">Reset Age</button>

      <!-- IF : Afficher "Majeur" SI age >= 18, SINON afficher "Mineur" -->
      <!-- Deux paragraphes, qui s'afficheront ou pas en fonction de l'age -->
      <!-- <p v-if="utilisateur.age >= 18">Majeur</p> -->
      <p v-if="isMajeur()">Majeur</p>
      <p v-else>Mineur</p>

      <p>{{ strMajeur() }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  
  // data => Données
  data() {
    // Nos données, utilisables dans notre template
    return {
      // utilisateur: "Jérémy"
      utilisateur: {
        username: "Jérémy",
        age: 28
      }
    }
  },

  // methods => les fonctionnalités
  methods: {
    demoClick() {
      // alert("On a cliqué ici ...");
      // Accès au contexte du fichier Vue avec le mot-clé 'this'
      this.utilisateur.username = "Défaut";
    },

    resetAge(age) {
      this.utilisateur.age = age;
    },

    isMajeur() {
      return (this.utilisateur.age >= 18);
    },

    strMajeur() {
      // if (this.utilisateur.age >= 18) {
      //   return "MAJEUR";
      // }

      // return "MINEUR";

      return (this.utilisateur.age >= 18) ? "MAJEUR" : "MINEUR";
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
