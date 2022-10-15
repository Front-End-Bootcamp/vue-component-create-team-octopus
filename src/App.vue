<script setup>

import { ref } from 'vue'
import Autocomplete from './components/Autocomplete.vue';
import Cookie from "./components/Cookie.vue";

const feedback = ref();

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
		<Teleport to="body">
		<Cookie title="Çerezleri kabul et" text="Bizler, güvenliğinize önem veriyor ve bu Çerez Politikası ile siz sevgili ziyaretçilerimizi,
		 web sitemizde hangi çerezleri, hangi amaçla kullandığımız ve çerez ayarlarınızı nasıl değiştireceğiniz konularında kısaca bilgilendirmeyi hedefliyoruz.
		 Sizlere daha iyi hizmet verebilmek adına, çerezler vasıtasıyla, ne tür kişisel verilerinizin hangi amaçla toplandığı ve nasıl işlendiği konularında,
		 kısaca bilgi sahibi olmak için lütfen bu Çerez Politikasını okuyunuz.
		 Daha fazla bilgi için Gizlilik Politikamıza göz atabilir ya da bizlerle çekinmeden iletişime geçebilirsiniz." v-model:feedback="feedback"></Cookie>
	</Teleport>
		<Autocomplete :options="productList" v-model:select="selectProduct" placeholder="Search product"></Autocomplete>
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