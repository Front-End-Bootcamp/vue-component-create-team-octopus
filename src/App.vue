<script setup>
import { ref } from 'vue'
import Autocomplate from './components/Autocomplate.vue';

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
		<Autocomplate :options="productList" v-model:select="selectProduct" placeholder="Search product"></Autocomplate>
	</div>
</template>

<style>
.container {
	padding-top: 15%;
	display: flex;
	justify-content: center;
	align-items: flex-start;
	height: 100vh;
	background-image: linear-gradient(-45deg, #ffffff, #ffffff 50%, #f6f6f6 50%, #f6f6f6);
	background-size: 7px 7px;
}
</style>