<script lang="ts">
	import type { PostType } from '../../lib/types';

	export let post: PostType;
</script>

<div class="container">
	<div class="postHeader">{post.postHeader}</div>
	<div class="postText">{post.postText}</div>
	<div><span>Создан: </span>{post.created}</div>
	{#if post?.edited}
		<div><span>Изменен: </span>{post?.edited}</div>
	{/if}
</div>

<style>
	.container {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 10px;
		border: 1px solid black;
		border-radius: 5px;
		padding: 5px;
		width: 500px;
	}
	.postHeader {
		font-weight: bold;
		font-size: 24px;
	}
	.postText {
		font-size: 20px;
	}
	@media screen and (max-width: 768px) {
		.container {
			display: flex;
			flex-direction: column;
			align-items: center;
			width: 300px;
			margin: auto;
		}
		.postHeader {
			font-weight: bold;
			font-size: 24px;
		}
	}
</style>
