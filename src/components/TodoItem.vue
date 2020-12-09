<template>
	<div class="todo-item" v-bind:class="{ 'is-complete': todo.completed }">
		<p>{{ todo.title }}</p>
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
}
.is-complete {
    text-decoration: line-through;
}
.checkbox {
	transform: scale(2);
    margin: 1em;
}
.del {
	background-color: red;
	color: white;
	font-size: 1em;
	border-radius: 50px;
	padding: 10px 45px 10px 45px;
}
</style>
