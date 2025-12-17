<template>
	<div class="editor-wrapper">
		<DragHandle v-if="showDragHandle" :editor="editor">
			<div>⠿</div>
		</DragHandle>
		<EditorContent :editor="editor" />
	</div>
</template>

<script>
import { Editor, EditorContent } from '@tiptap/vue-2'
import StarterKit from '@tiptap/starter-kit'
import DragHandle from '@tiptap/extension-drag-handle-vue-2'

export default {
	name: 'TiptapEditor',
	components: {
		DragHandle,
		EditorContent,
	},
	data() {
		return {
			editor: null,
			editorReady: false,
			selectedNode: null,
		}
	},
	computed: {
		showDragHandle() {
			return this.editor
				&& this.editorReady
		},
	},
	mounted() {
		this.editor = new Editor({
			extensions: [
				StarterKit,
			],
			content: `
				<h1>Tiptap with Drag Handle</h1>
				<p>This is a paragraph</p>
				<p>Another paragraph</p>
			`,
		})

		this.$nextTick(() => {
			this.editorReady = true
		})
	},
	beforeDestroy() {
		this.editor?.destroy()
	},
}
</script>

<style lang="scss" scoped>
.editor-wrapper {
	position: relative;
	border: 1px solid #ccc;
	border-radius:	8px;
	padding:	50px;
}

/* Basic Tiptap styles */
.editor-wrapper :deep(.ProseMirror) {
	outline: none;
	min-height: 350px;

	h1 {
		font-size: 2em;
		margin:	0.67em 0;
	}

	p {
		margin: 0.5em 0;
	}

	ul, ol {
		padding: 0 1rem;
	}
}
</style>
