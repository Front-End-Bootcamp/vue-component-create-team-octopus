<script setup>
import { ref } from 'vue';
import Autocomplete from './components/Autocomplete.vue';
import Cookie from "./components/Cookie.vue";
import Pupup from './components/Pupup.vue';

const showPopup = ref(false);
const showImagePopup = ref(false);
const showVideoPopup = ref(false);
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
		 Daha fazla bilgi için Gizlilik Politikamıza göz atabilir ya da bizlerle çekinmeden iletişime geçebilirsiniz."
				v-model:feedback="feedback"></Cookie>
		</Teleport>

		<div class="btn-group">
			<button class="btn btn--positive" @click="showPopup = true">Show Popup</button>
			<button class="btn btn--positive" @click="showImagePopup = true">İmage Popup</button>
			<button class="btn btn--positive" @click="showVideoPopup = true">Video Popup</button>
		</div>

		<Autocomplete :options="productList" v-model:select="selectProduct" placeholder="Search product"></Autocomplete>
		<Teleport to="body">
			<Pupup title="Title" text="Text" v-model:show="showPopup" negative-text="Cancel" positive-text="Accept" closable
				@positive-click="" @negative-click="">
			</Pupup>
			<Pupup title="Title" text="Text" v-model:show="showImagePopup" negative-text="Cancel" positive-text="Accept"
				closable @positive-click="" @negative-click="">
				<template #body>
					<img src="https://picsum.photos/300/200" alt="" class="img-fluid">
				</template>
			</Pupup>
			<Pupup title="Title" text="Text" v-model:show="showVideoPopup" negative-text="Cancel" positive-text="Accept"
				closable @positive-click="" @negative-click="">
				<template #body>
					<iframe width="452" height="300" src="https://www.youtube.com/embed/9bZkp7q19f0" frameborder="0"
						allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
						allowfullscreen></iframe>
				</template>
			</Pupup>
		</Teleport>
	</div>
</template>

<style>
.container {
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	height: 100vh;
	background-image: linear-gradient(-45deg, #ffffff, #ffffff 50%, #f6f6f6 50%, #f6f6f6);
	background-size: 7px 7px;
	gap: 24px;
}
</style>
