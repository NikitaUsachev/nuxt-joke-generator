<template>
	<div>
		<UButton color="info" @click="getJoke">New joke</UButton>
		<JokeCard :joke="currentJoke"/>
		<HistoryList :history='jokeHistory' @remove="removeJoke"/>
	</div>
</template>

<script setup>
import { ref } from "vue";
import JokeCard from "~/components/JokeCard.vue";
import HistoryList from "~/components/HistoryList.vue";

//текущая штука
const currentJoke = ref('')
// Храним все предыдущие шутки
const jokeHistory = ref([])

// Получаем шутку
const getJoke = async () => {
	try {
		const response = await $fetch('https://icanhazdadjoke.com/', {
			headers: {Accept: 'application/json'},
		});
		currentJoke.value = response.joke
		jokeHistory.value.unshift(response.joke) // шутку добавляем в начало
		jokeHistory.value = jokeHistory.value.slice(0, 5) // сохраняем 5 последних
	} catch (error) {
		currentJoke.value = 'Ошибка'
	}
}

//Удалить шутку
const removeJoke = (index) => {
	jokeHistory.value.splice(index, 1)
}
//При загрузке покажет первую шутку
onMounted(() => {
	getJoke()
})

</script>