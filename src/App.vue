<script setup>
import Cookie from "./components/Cookie.vue";
import { ref } from "vue";

const feedback = ref();
</script>

<template>
	<Teleport to="body">
		<Cookie text="Çerezleri kabul et" v-model:feedback="feedback"></Cookie>
	</Teleport>
</template>

<style lang="scss">

</style>