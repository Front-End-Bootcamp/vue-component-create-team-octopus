<script setup>
const props = defineProps({
	title: { type: String, default: undefined },
	text: { type: String },
	show: { type: Boolean, default: false },
	negativeText: { type: String, default: undefined },
	positiveText: { type: String, default: undefined },
	closable: { type: Boolean, default: false },
});
const emit = defineEmits(['positive-click', 'negative-click', 'update:show']);

const closeHandler = () => {
	emit('update:show', false);
	return;
};
const negativeHandler = () => {
	emit('negative-click');
	closeHandler();
};
const positiveHandler = () => {
	emit('positive-click');
	closeHandler();
};
</script>

<template>
	<div class="popup" v-if="props.show">
		<div class="popup__mask"></div>
		<div class="popup__content">
			<div class="popup__content-header">
				<h3 v-if="props.title != undefined">{{ props.title }}</h3>
				<button v-if="closable" class="popup__content-close" @click="closeHandler">
					<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
						<path d="M18 6L6 18" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
						<path d="M6 6L18 18" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
					</svg>
				</button>
			</div>
			<div class="popup__content-body">
				<slot name="body">
					{{props.text}}
				</slot>
			</div>
			<div class="popup__content-action">
				<slot name="action">
					<button class="btn btn--negative" v-if="props.negativeText != undefined" @click="negativeHandler">{{
					props.negativeText }}</button>
					<button class="btn btn--positive" v-if="props.positiveText != undefined" @click="positiveHandler">{{
					props.positiveText }}</button>
				</slot>
			</div>
		</div>
	</div>
</template>

<style lang="scss">
.popup {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	z-index: 999;

	&__mask {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: rgba(0, 0, 0, 0.5);
	}

	&__content {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 100%;
		max-width: 500px;
		background-color: #fff;
		border-radius: 6px;
		padding: 24px;
		display: flex;
		flex-direction: column;
		gap: 24px;

		&-header {
			display: flex;
			align-items: center;
			justify-content: space-between;

			h3 {
				font-size: 18px;
				font-weight: 500;
				color: #000;
			}
		}

		&-close {
			width: 24px;
			height: 24px;
			background-color: transparent;
			border: none;
			cursor: pointer;
			margin-left: auto;

			svg {
				width: 100%;
				height: 100%;

				path {
					stroke: #000;
				}
			}
		}

		.popup__content-action {
			display: flex;
			align-items: center;
			justify-content: flex-end;
			gap: 16px;
		}
	}
}

.btn {
	cursor: pointer;
	padding: 8px 16px;
	border: 0;
	border-radius: 4px;

	&--negative {
		color: #fff;
		background-color: #f44336;
	}

	&--positive {
		color: #fff;
		background-color: #4caf50;
	}
}
</style>
