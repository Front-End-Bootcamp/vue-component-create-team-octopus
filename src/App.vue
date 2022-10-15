<script setup>
import Cookie from "./components/Cookie.vue";
import { ref } from "vue";

const feedback = ref();
</script>

<template>
	<Teleport to="body">
		<Cookie title="Çerezleri kabul et" text="Bizler, güvenliğinize önem veriyor ve bu Çerez Politikası ile siz sevgili ziyaretçilerimizi,
		 web sitemizde hangi çerezleri, hangi amaçla kullandığımız ve çerez ayarlarınızı nasıl değiştireceğiniz konularında kısaca bilgilendirmeyi hedefliyoruz.
		 Sizlere daha iyi hizmet verebilmek adına, çerezler vasıtasıyla, ne tür kişisel verilerinizin hangi amaçla toplandığı ve nasıl işlendiği konularında,
		 kısaca bilgi sahibi olmak için lütfen bu Çerez Politikasını okuyunuz.
		 Daha fazla bilgi için Gizlilik Politikamıza göz atabilir ya da bizlerle çekinmeden iletişime geçebilirsiniz." v-model:feedback="feedback"></Cookie>
	</Teleport>
</template>

<style lang="scss">

</style>