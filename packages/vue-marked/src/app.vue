<template>
	<h1>Hello Vue 3!asdfasdf</h1>
    <div v-html="markHtml"></div>
	<textarea  v-model="markStr" class="mark-text"></textarea>
	
</template>

<script>
	import { ref, watch } from "vue";
	import marked from "marked";
	
	export default {
		setup() {
			const markHtml = ref('')
			const markStr = ref('')

			watch(markStr, val => {
				markHtml.value = marked(val)
			})

			return {
				markHtml,
				markStr,
			};
		},
	};
</script>

<style scoped>
	img {
		width: 200px;
	}
	h1 {
		font-family: Arial, Helvetica, sans-serif;
	}
	.mark-text {
		width: 200px;
		height: 600px;
	}

</style>