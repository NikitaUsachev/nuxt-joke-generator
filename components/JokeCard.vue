<template>
	<div class="joke-card">
		<p>{{ joke }}</p>
	</div>
</template>

<script setup>
defineProps({
	joke: String,
})
</script>

<style scoped>
.joke-card {
	background: #F0F0F0;
	padding: 20px;
	border-radius: 12px;
	margin: 20px 0;
	font-size: 1.1rem;
	font-style: italic;
}

</style>