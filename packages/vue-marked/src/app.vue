<template>
	<h1>Hello Vue 3!asdfasdf</h1>
	<button @click="inc">Clicked {{ count }} times.</button>
    <div v-html="markHtml"></div>
</template>

<script>
	import { ref } from "vue";
	import marked from "marked";
	export default {
		setup() {
			console.log(marked);
            const count = ref(0);
            const markHtml = ref('')
			const inc = () => {
                count.value++;
			    markHtml.value = marked("# Marked in the browser\n\nRendered by **marked**.");
			};
			return {
				count,
                inc,
                markHtml,
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
</style>