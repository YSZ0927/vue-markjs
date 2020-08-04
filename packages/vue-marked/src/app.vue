<template>
	<div class="header">
		<input type="text" placeholder="输入文章标题">
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
	.header{
		display: flex;
		justify-content: space-between;
		padding: 10px 0;
	}
	.edit-area {
		display: flex;
	}
	.mark-text {
		width: 50%;
		height: calc(100vh - 100px);
		background: #333;
		color: antiquewhite;
		padding: 20px
	}
	.html-show {
		width: 50%;
		border: 1px solid #ccc;
		padding: 20px;
	}
	
</style>