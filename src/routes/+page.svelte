<script lang="ts">
	import AddPostForm from './components/AddPostForm.svelte';
	import PostList from './components/PostList.svelte';
	import type { PostType } from '../lib/types';
	import { onMount } from 'svelte';
	let posts: PostType[] = [];
	onMount(() => {
		let data = localStorage.getItem('posts');
		if (data) {
			posts = JSON.parse(data);
		}
	});
</script>

<div class="container">
	<AddPostForm
		{posts}
		on:add_post={(event) => {
			posts = event.detail;
		}}
	/>
	<PostList {posts} />
</div>

<style>
	.container {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 50px;
	}
</style>
