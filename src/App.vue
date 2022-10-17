<script setup>
import { ref } from 'vue';
import Pupup from './components/Pupup.vue';

const showPopup = ref(false);
</script>

<template>
	<Teleport to="body">
		<Pupup title="Title" text="Text" v-model:show="showPopup" negative-text="Cancel" positive-text="Ok" closable
			@positive-click="" @negative-click="">
		</Pupup>
	</Teleport>
</template>
