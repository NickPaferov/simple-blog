<script lang="ts">
	import type { PostType } from '../../lib/types';

	export let post: PostType;
</script>

<div class="item">
	<span class="postHeader">{post.postHeader}</span>
	<div class="date">
		<span>Создан: {post.created}</span>
		{#if post.edited}
			<span>Изменен: {post.edited}</span>
		{/if}
	</div>
</div>

<style>
	.item {
		display: flex;
		justify-content: space-between;
		align-items: center;
		width: 500px;
		border: 1px solid black;
		border-radius: 5px;
		padding: 5px;
	}
	.postHeader {
		font-weight: bold;
		font-size: 20px;
	}
	.date {
		display: flex;
		flex-direction: column;
	}
</style>
