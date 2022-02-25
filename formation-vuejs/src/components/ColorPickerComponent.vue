<template>
	<div>
		<div>- Choisir une couleur ({{ couleurActive }}) -</div>
		<select v-model="couleurActive" @change="changerCouleur">
			<option	v-for="couleur of couleurs"
					:key="couleur"
					:value="couleur"
			>{{ couleur }}</option>
		</select>
	</div>
</template>

<script>
export default {
	data() {
		return {
			couleurActive: 'black',
			couleurs: [ 'black', 'red', 'yellow', 'blue' ]
		}
	},

	methods: {
		changerCouleur() {
			this.$emit('changement', this.couleurActive);
			// alert('Changement ! La couleur changée est : ' + this.couleurActive);
		}
	}
}
</script>