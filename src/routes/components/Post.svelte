<script lang="ts">
	import type { PostType } from '../../lib/types';
	import ShortPost from './ShortPost.svelte';
	import DetailedPost from './DetailedPost.svelte';
	import EditPostForm from './EditPostForm.svelte';

	export let post: PostType;

	let readMode: boolean = false;
	const onReadMode = () => {
		readMode = true;
	};
	const offReadMode = () => {
		readMode = false;
	};

	let editMode: boolean = false;
	const onEditMode = () => {
		editMode = true;
	};
	const offEditMode = () => {
		editMode = false;
	};
</script>

<div class="container">
	{#if readMode}
		{#if editMode}
			<div class="editMode">
				<EditPostForm
					{post}
					on:edit_post={(event) => {
						post = event.detail;
						offEditMode();
					}}
				/>
				<button on:click={offEditMode}>Вернуться</button>
			</div>
		{:else}
			<DetailedPost {post} />
			<div class="btnBlock">
				<button on:click={offReadMode}>Свернуть</button>
				<button on:click={onEditMode}>Редактировать</button>
			</div>
		{/if}
	{:else}
		<ShortPost {post} />
		<button on:click={onReadMode}>Читать</button>
	{/if}
</div>

<style>
	.container {
		display: flex;
		gap: 10px;
	}
	.editMode {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 10px;
	}
	.btnBlock {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
</style>
