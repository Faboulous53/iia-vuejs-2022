<template>
	<div>
		<h1>TODO LIST</h1>

		<todo	v-for="todo of todos"
				:key="todo.id"
				:todo="todo" />
	</div>
</template>

<script>
// @ fait revenir au répertoire "src"
// import Todo from '../components/TodoComponent.vue';
import Todo from '@/components/TodoComponent.vue';

export default {
	components: {
		Todo
	},

	data() {
		return {
			todos: [
				{ id: 1, title: "OK", completed: false },
				{ id: 2, title: "OK 2", completed: true },
				{ id: 3, title: "OK 3", completed: false },
			]
		}
	}
}
</script>