<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
    
    <div>
      <h1>Intro</h1>

      Hello {{ utilisateur.username }}, vous avez {{ utilisateur.age }} ans !
      <div>
        <input type="text" v-model="utilisateur.username" />
        <input type="number" v-model="utilisateur.age" />
      </div>

      <!-- v-bind:attrName -->
      <!-- :attrName -->
      <!-- <p v-bind:class="utilisateur.username"> -->
      <p :class="{ 'demo-bind': utilisateur.username === 'jeremy' }">
        Un texte en exemple qui changera de couleur.
      </p>

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

      <hr />

      <h1>Boucles</h1>
      Un prénom => {{ prenoms[0] }}

      <button @click="ajouterPrenom()">Ajouter un prénom</button>

      <ul>
        <li v-for="prenom of prenoms" v-bind:key="prenom">
          {{ prenom }}
        </li>
      </ul>

      <hr />

      <!-- Composant :propName="objetConnu" -->
      <crud-utilisateur
        :utilisateurs="utilisateurs"
        @ajout="ajouterUtilisateur"
        @supprime="supprimerUtilisateur" />

      <hr />

      <h1>Composant</h1>

      <message :msg="utilisateurs[0].username" />

      <hr />

      <color-picker @changement="changementCouleur" />
    </div>
  </div>
</template>

<script>
import Message from './components/MessageComponent.vue';
import CrudUtilisateur from './components/CrudUtilisateurComponent.vue';
import ColorPicker from './components/ColorPickerComponent.vue';

export default {
  name: 'App',

  components: {
    Message, CrudUtilisateur, ColorPicker
  },
  
  // data => Données
  data() {
    // Nos données, utilisables dans notre template
    return {
      // utilisateur: "Jérémy"
      utilisateur: {
        username: "Jérémy",
        age: 28
      },

      prenoms: [
        "Marion", "Mickael", "Aurélie", "Delphine"
      ],

      utilisateurs: [
        { username: "Toto",   age: 20 },
        { username: "Albert", age: 25 },
        { username: "Jérôme", age: 30 }
      ]
    }
  },

  // methods => les fonctionnalités
  methods: {
    demoClick() {
      // alert("On a cliqué ici ...");
      // Accès au contexte du fichier Vue avec le mot-clé 'this'
      this.utilisateur.username = "";
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
    },

    ajouterPrenom() {
      this.prenoms.push(this.utilisateur.username);

      //Reset le "form"
      this.demoClick();
      // this.utilisateur.username = "";
    },

    ajouterUtilisateur(user) {
      // On va lui demander de faire une copie des attributs
      this.utilisateurs.push({ ...user });
    },

    supprimerUtilisateur(user) {
      let index = this.utilisateurs.indexOf(user);

      // On supprime 1 utilisateur, à partir de l'index
      this.utilisateurs.splice(index, 1);
    },

    changementCouleur(couleur) {
      alert('Changement ! La couleur sélectionnée est : ' + couleur);
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

.demo-bind {
  color: red;
}


</style>
