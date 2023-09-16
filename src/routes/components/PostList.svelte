<script lang="ts">
	import { onMount } from 'svelte';
	import type { PostType } from '../../lib/types';
	import Post from './Post.svelte';

	export let posts: PostType[];
</script>

<div class="container">
	{#if posts.length}
		<h1>Список постов</h1>
		<div class="list">
			{#each posts as post (post.id)}
				<Post {post} />
			{/each}
		</div>
	{:else}
		<div class="notification">У вас ещё нет постов</div>
	{/if}
</div>

<style>
	.container {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.list {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 10px;
	}
	.notification {
		margin: 20px;
		font-size: 30px;
		opacity: 0.7;
	}
	@media screen and (max-width: 768px) {
		.list {
			gap: 30px;
		}
	}
</style>
