<script lang="ts">
	import type { PostType } from '../../lib/types';
	import { createEventDispatcher } from 'svelte';

	export let post: PostType;
	
	const dispatch = createEventDispatcher();

	let postHeaderValue: string = post.postHeader;
	let postTextValue: string = post.postText;

	let data = localStorage.getItem('posts');
	let posts: PostType[] = [];
	if (data) {
		posts = JSON.parse(data);
		console.log(posts);
	}
	let currentPost = posts.find((p) => p.id === post.id);
	let currentPostIndex: number;
	if (currentPost) {
		currentPostIndex = posts.indexOf(currentPost);
	}

	const editPost = () => {
		let edited = new Date().toLocaleString();
		let editedPostHeader = postHeaderValue.trim();
		let editedPostText = postTextValue.trim();
		let editedPost = {
			id: post.id,
			postHeader: editedPostHeader,
			postText: editedPostText,
			created: post.created,
			edited
		};
		posts.splice(currentPostIndex, 1, editedPost);
		localStorage.setItem('posts', JSON.stringify(posts));
		dispatch('edit_post', editedPost);
	};
</script>

<form on:submit={editPost}>
	<input type="text" placeholder="Введите заголовок поста" bind:value={postHeaderValue} required />
	<textarea placeholder="Введите текст поста" bind:value={postTextValue} required />
	<button type="submit">Сохранить</button>
</form>
