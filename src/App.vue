<script setup>
import { ref } from 'vue'
import AutoComplate from './components/AutoComplate.vue';

const productList = [
	'Apple',
	'Apricot',
	'Avocado',
	'Banana',
	'Blackberry',
	'Boysenberry',
	'Cantaloupe',
	'Cherry',
	'Clementine',
	'Damson',
	'Date',
	'Dragonfruit',
];
const selectProduct = ref('');
</script>

<template>
	<div class="container">
		<AutoComplate :options="productList" v-model:select="selectProduct" placeholder="Search product"></AutoComplate>
	</div>
</template>

<style>
.container {
	display: flex;
	justify-content: center;
	align-items: center;
	height: 100vh;
}
</style>