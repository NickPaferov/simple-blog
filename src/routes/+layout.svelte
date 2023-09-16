<div class="app">
	<header>
		<a href="/">Мой блог</a>
	</header>
	<div>
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
	}
	footer {
		font-size: 20px;
		padding: 5px;
	}
	a {
		color: white;
		text-decoration: none;
	}
</style>
