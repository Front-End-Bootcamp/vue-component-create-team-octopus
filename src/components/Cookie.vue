<script setup>
import { computed } from "vue"
const props = defineProps(['text','feedback']);
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
		<div class="cookie__content">
			{{props.text}}
		</div>
		<button class="cookie__button" @click="clickHandler">
			Accept
		</button>
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
  padding: 8px;
  border-radius: 8px;
  gap: 24px;

  &__content {
    color: #fff;
		width: 100%;
  }

  &__button {
    padding: 4px 8px;
    text-transform: uppercase;
    background-color: royalblue;
    color: #fff;
    cursor: pointer;
    border: none;
    border-radius: 6px;
  }
}
</style>