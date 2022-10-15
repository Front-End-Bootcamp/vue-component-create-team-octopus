<script setup>
import { computed } from "vue"
const props = defineProps(['title','text','feedback']);
const emit = defineEmits(['update:feedback']);

const clickHandler = () => {
	emit('update:feedback', true);
	let date = new Date(Date.now() + 86400e3);
	date = date.toUTCString();
	document.cookie = "cookie=accept; expires=" + date;
};

const show = computed(() => {
	const feedback = document.cookie.split(';').some((item) => item.trim().startsWith('cookie='));
  console.log(feedback);

  if (feedback) {
    return false;
  } else if (props.feedback) {
    return false;
  }
  return true;
}) 
</script>

<template>
	<div class="cookie" v-if="show" >
		<slot>
			<div class="cookie__content">
				<div class="cookie__header">
				{{props.title}}
				</div>
				<div class="cookie__text">
				{{props.text}}
				</div>
			</div>
		<button class="cookie__button" @click="clickHandler">
			Accept
		</button>
		</slot>
	</div>
</template>

<style lang="scss">
.cookie {
  position: fixed;
  left: 16px;
	right: 16px;
  bottom: 16px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: rgba(0, 0, 0, 0.377);
  padding: 50px;
  border-radius: 8px;
  gap: 24px;

  &__content {
    color: #fff;
		width: 100%;
  }
	&__header {
    color: #fff;
		width: 100%;
		font-size: 30px;
		font-weight: bold;
		padding-bottom: 15px;
  }
  &__button {
    padding: 15px 30px;
    text-transform: uppercase;
    background-color: royalblue;
    color: #fff;
    cursor: pointer;
    border: none;
    border-radius: 6px;
  }
	&__text {
		font-size: large;
	}
}
</style>