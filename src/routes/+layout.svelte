<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.ico';
	import Kanneli from '$lib/assets/svg/Kanneli.svelte'

	import { page } from '$app/state';
	let { children } = $props();
	
	function isActive(path: string) {
		return page.url.pathname === path;
	}
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<div id="navbar">
	<a href="/" title="home">
		<div class:active={isActive('/')} class="nav-button home">
			<span class="home-icon">
				<Kanneli />
			</span>
		</div>
	</a>
	<a href="/about" title="about">
		<div class:active={isActive('/about')} class="nav-button">
			<span class="icon-[mingcute--user-2-fill]"></span>
		</div>
	</a>
	<a href="/posts" title="posts">
		<div class:active={isActive('/posts')} class="nav-button">
			<span class="icon-[mingcute--chat-1-fill]"></span>
		</div>
	</a>
</div>

<div id="page">
	<div id="content">
		{@render children()}
	</div>
</div>

<style>
	#page {
		display: flex;
		flex-direction: row;
		justify-content: center;
	}
	#navbar, #content {
		display: flex;
		flex-direction: column;
	}
	#navbar {
		row-gap: 15px;
		padding: 10px;
		position: fixed;
		top: 200px;
		left: 0;
		border-radius: 20px;
		background-color: #b62f46;
	}
	#content {
		width: 50vw;
		margin: 200px 0;
	}
	@media only screen and (max-width: 600px) {
		#navbar {
			display: flex;
			flex-direction: row;
			gap: 15px;
			margin: 0 5vw;
			position: fixed; 
			top: 5vw;
			left: 0px;
			width: 90vw;
		}
		#content {
			width: 80vw;
			margin: 140px 0;
		}
	}
	@media only screen and (min-width: 600px) {
		#navbar {
			top: 50px;
			margin: 0 25px
		}
		#content {
			width: 60vw;
			margin: 50px 0;
		}
	}
	@media only screen and (min-width: 1200px) {
		#navbar {
			top: 200px;
			margin: 0 50px;
		}
		#content {
			width: 50vw;
			margin: 200px 0;
		}
	}

    .nav-button {
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 1.6em;
        height: 50px;
        aspect-ratio: 1/1;
        border-radius: 15px;
        color: #e5d8bc;
		background: #b62f46;
		box-shadow:  -5px -5px 9px #641b28, 5px 5px 9px #f55670;
		transition: all 0.05s;
		transition-timing-function:ease-out;
    }
	
	.nav-button:hover {
		background: linear-gradient(145deg, #df435d, #862031);
	}
	.nav-button.active {
		color: #b62f46;
		background: #e0e0e0;
		box-shadow: inset -5px -5px 8px #a6a6a6, inset 5px 5px 8px #ffffff;
	}
	.nav-button.active.home, .nav-button.active .home-icon {
		color: black;
		fill: black;
	}
	.home-icon {
		fill: #e5d8bc;
		width: 30px;
	}
</style>