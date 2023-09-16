<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	import { v1 } from 'uuid';
	import type { PostType } from "../../lib/types";

	export let posts: PostType[]

	const dispatch = createEventDispatcher()

	let postHeaderValue: string = '';
	let postTextValue: string = '';
	

	const addPost = () => {
		let id = v1()
		let postHeader = postHeaderValue.trim()
		let postText = postTextValue.trim()
		let created = new Date().toLocaleString();
		posts.push({ id, postHeader, postText, created });
		localStorage.setItem('posts', JSON.stringify(posts));
		postHeaderValue = '';
		postTextValue = '';
		dispatch("add_post", posts)
	};
</script>

<div class="newPost">
	<h1>Создайте пост</h1>
	<form on:submit={addPost}>
		<input type="text" placeholder="Введите заголовок поста" bind:value={postHeaderValue} required />
		<textarea placeholder="Введите текст поста" bind:value={postTextValue} required />
		<button type="submit">Добавить пост</button>
	</form>
</div>

<style>
	.newPost {
		margin: auto;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	:global(form) {
		display: flex;
		flex-direction: column;
		align-items: center;
		width: 500px;
		gap: 10px;
	}
	:global(input,
	textarea) {
		font-size: 16px;
		padding: 5px;
		width: 100%;
		box-sizing: border-box;
	}
	:global(textarea) {
		height: 100px;
		resize: none;
	}
	:global(button) {
		font-size: 16px;
		background-color:mediumblue;
		color: white;
		width: 150px;
		padding: 10px;
		border-radius: 5px;
	}
</style>
