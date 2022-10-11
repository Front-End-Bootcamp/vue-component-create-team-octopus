<script setup>
import { ref, computed } from 'vue'
const props = defineProps({
	options: { type: Array, default: [] },
	select: { type: String, default: '' },
	placeholder: { type: String, default: '' }
});
const emit = defineEmits(['update:select']);

const results = ref([]);
const counter = ref(-1);

const inputHandler = (e) => {
	const { value } = e.target;
	emit('update:select', value);
	if (value.length > 0) {
		const matches = props.options.filter(option => {
			return option.toLowerCase().includes(value.toLowerCase())
		});
		results.value = matches;
		return;
	}
	counter.value = -1;
	results.value = [];
	return;
}
const clickHandler = (result) => {
	emit('update:select', result);
	results.value = [];
	return;
}
const keyupEnter = (e) => {
	const { value } = e.target;
	if (counter.value === -1) {
		emit('update:select', value);
		results.value = [];
	}
	emit('update:select', results.value[counter.value]);
	results.value = [];
	counter.value = -1;
	return;
}
const keyupEsc = () => {
	results.value = [];
	return;
}
const keyupDelete = () => {
	counter.value = -1;
	return;
}
const keyupArrowUp = () => {
	if (counter.value > 0) {
		counter.value--;
	}
	return;
}
const keyupArrowDown = () => {
	if (counter.value < results.value.length - 1) {
		counter.value++;
	}
	return;
}

const show = computed(() => {
	return results.value.length > 0;
});

</script>

<template>
	<div class="autocomplate" :class="{'active' : show}">
		<input type="text" class="autocomplate__input" :value="props.select" :placeholder="props.placeholder"
			@input="inputHandler" @keyup.enter="keyupEnter" @keyup.esc="keyupEsc" @keyup.arrow-up="keyupArrowUp"
			@keyup.arrow-down="keyupArrowDown" @keyup.delete="keyupDelete">
		<div class="autocomplate__wrapper" v-if="show">
			<div class="autocomplate__item" v-for="(result, index) in results" :key="index">
				<span @click="clickHandler(result)" :class="{'active': index === counter}">⌕ {{result}}</span>
			</div>
			<div class="autocomplate__footer">
				<b>⇅</b> to navigate, <b>↲</b> to select, <b>esc</b> to close
			</div>
		</div>
	</div>
</template>

<style lang="scss">
.autocomplate {
	position: relative;
	border-radius: 8px;
	transition: all 0.3s ease-in-out;

	&__input {
		width: 100%;
		padding: 10px 14px;
		border: 0;
		border-radius: 8px;
		background-color: #ffffff;
		border: 2px solid #f7e7e5;
		min-width: 320px;
		transition: all 0.3s ease-in-out;

		&:focus {
			outline: none;
		}
	}

	&__wrapper {
		position: absolute;
		top: 100%;
		left: 0;
		width: 100%;
		background-color: whitesmoke;
		border-radius: 0 0 8px 8px;

		box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
		border: 2px solid #f7e7e5;
		border-top: 0;
		display: flex;
		flex-direction: column;
		gap: 4px;

	}

	&__footer {
		font-size: 12px;
		color: gray;
		text-align: center;
		margin-top: 6px;

		b {
			color: royalblue;
		}
	}

	&__item {
		width: 100%;

		span {
			padding: 2px 12px;
			cursor: pointer;
			font-size: 12px;
			width: 100%;
			display: block;

			&:hover {
				background-color: #f7e7e5;
			}

			&.active {
				background-color: #f7e7e5;
			}
		}
	}

	&.active {
		box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;

		.autocomplate__input {
			border-radius: 8px 8px 0 0;
		}
	}
}
</style>
