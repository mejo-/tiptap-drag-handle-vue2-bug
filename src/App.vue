<script setup lang="ts">
import TiptapEditor from './components/TiptapEditor.vue'
</script>

<template>
	<div id="app">
		<header>
		<h1>Tiptap DragHandle Vue Bug Demo</h1>
		</header>

		<main>
			<TiptapEditor />
		</main>
	</div>
</template>

<style scoped>
header {
	line-height: 1.5;
}

#app {
	display: flex;
	flex-direction: column;
}
</style>
