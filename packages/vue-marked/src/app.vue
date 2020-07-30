<template class="asdf">
	<div>
		<button>发布</button>
	</div>
	<div class="edit-area">
		<textarea  v-model="markStr" class="mark-text"></textarea>
		<div class="html-show" v-html="markHtml"></div>
	</div>
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
	.edit-area {
		display: flex;
	}
	.mark-text {
		width: 50;
		height: calc(100vh - 100px);
		background: #333;
		flex: 1;
		color: antiquewhite;
	}
	.html-show {
		width: 600px;
		border: 1px solid #ccc;
	}
	
</style>