<div class="app">
	<header>
		<span>Мой блог</span>
	</header>
	<div class="content">
		<slot />
	</div>
	<footer>
		<span>Николай Паферов</span>
	</footer>
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		min-height: 100vh;
		overflow: scroll;
	}
	header,
	footer {
		display: flex;
		justify-content: center;
		width: 100%;
		background-color: darkslategrey;
		color: white;
	}
	header {
		font-size: 30px;
		padding: 10px;
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
	}
	.content {
		margin-top: 50px;
		margin-bottom: 40px;
	}
	footer {
		font-size: 20px;
		padding: 5px;
		position: fixed;
		bottom: 0;
		left: 0;
		right: 0;
	}
</style>
