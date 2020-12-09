<template>
	<div class="todo-item" v-bind:class="{ 'is-complete': todo.completed }">
		<h2>{{ todo.title }}</h2>
		<div>
			<input
				type="checkbox"
				class="checkbox"
				v-on:change="markComplete"
                v-bind:checked="todo.completed"
			/>
		</div>
		<div>
			<button class="del" @click="$emit('del-todo', todo.id)">Delete</button>
		</div>
	</div>
</template>

<script>
export default {
	name: "TodoItem",
	props: ["todo"],
	methods: {
		markComplete() {
			this.todo.completed = !this.todo.completed;
		},
	},
};
</script>

<style scoped>
.todo-item {
    font-weight: 700;
    background: lightblue;
    border-radius: 1em;
    margin: 0.5em;
    padding: 0.5em;
}
.is-complete {
    text-decoration: line-through;
}
.checkbox {
	transform: scale(2.5);
    margin: 2em;
}
.del {
	background-color: red;
	color: white;
    width: 100%;
	font-size: 1em;
	border-radius: 50px;
	padding: 10px;
}
</style>
