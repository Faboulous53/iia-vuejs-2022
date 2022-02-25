<template>
	<div>
		<h1>Liste des utilisateurs</h1>

		<div>
			<label>Nom d'utilisateur</label>
			<input type="text" v-model="formUtilisateur.username" />
		</div>

		<div>
			<label>Age</label>
			<input type="number" v-model="formUtilisateur.age" />
		</div>

		<!-- <div v-if="formUtilisateur.username.length >= 5 && formUtilisateur.age > 0">
			<button @click="ajouterUtilisateur()">Ajouter l'utilisateur</button>
		</div> -->

		<div>
			<button :disabled="!formUtilisateur.username || formUtilisateur.age <= 0" @click="ajouterUtilisateur()">Ajouter l'utilisateur</button>
		</div>
		
		
		<table>
			<thead>
				<tr>
					<th>Nom</th>
					<th>Age</th>
					<th></th>
				</tr>
			</thead>

			<tbody>
				<tr v-for="user of utilisateurs" :key="user.username">
					<td>{{ user.username }}</td>
					<td>{{ user.age }}</td>
					<td>
						<button @click="supprimerUtilisateur(user)">Supprimer</button>
					</td>
				</tr>
			</tbody>
		</table>
	</div>
</template>

<script>
export default {
	// Données en entrée (props)
	props: {
		utilisateurs: Array
	},

	// Données internes (data)
	data() {
		return {
			formUtilisateur: {
				username: "",
				age: 0
			}
		}
	},

	// Fonctionnalités (methods)
	methods: {
		ajouterUtilisateur() {
			this.$emit('ajout', this.formUtilisateur);
		},

		supprimerUtilisateur(user) {
			this.$emit('supprime', user);
		}
	}
}
</script>