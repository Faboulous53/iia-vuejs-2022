<template>
	<div>
		<h1>Titre</h1>
		FORM
		
		
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
	}

	// Données internes (data)

	// Fonctionnalités (methods)
}
</script>