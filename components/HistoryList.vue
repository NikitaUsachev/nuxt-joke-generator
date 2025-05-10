<template>
	<div v-if="history.length" class="history">
		<h2>Joke history:</h2>
		<ul>
			<li v-for="(joke, index) in history" :key="index">
				{{ joke }}
				<button @click="remove(index)">Delete</button>
			</li>
		</ul>
	</div>
</template>

<script setup>
defineProps({
	history: Array
})

const emit = defineEmits(['remove'])

const remove = (index) => {
	emit('remove', index)
}

</script>

<style scoped>
.history {
	margin-top: 20px;
	text-align: left;
}
.history ul {
	padding-left: 20px;
}
.history li {
	margin-bottom: 10px;
	font-size: 0.95rem;
}
</style>