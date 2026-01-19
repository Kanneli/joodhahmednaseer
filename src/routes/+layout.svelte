<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.ico';

	import { page } from '$app/state';
	import { onMount } from "svelte";

	let { children } = $props();

	function isActive(path: string) {
    	return page.url.pathname === path;
  	}
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<div id="page">
	<div id="navbar">
		<a href="/" title="home">
			<div class:active={isActive('/')} class="nav-button home">
				<span class="icon-[mingcute--home-1-fill]"></span>
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
		margin: 0 50px;
		padding: 10px;
		position: fixed;
		top: 200px;
		left: 0;
		border-radius: 20px;
		background-color: #d6593a;
	}
	#content {
		width: 50vw;
		margin-top: 200px;
	}

    .nav-button {
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 2em;
        height: 50px;
        aspect-ratio: 1/1;
        border-radius: 15px;
        color: #e5d8bc;
		background: #d6593a;
		box-shadow:  -5px -5px 9px #ab472e, 5px 5px 9px #ff6b46;
		transition: all 0.05s;
		transition-timing-function:ease-out;
    }
	
	.nav-button:hover {
		background: linear-gradient(315deg, #b14328, #f77352);
	}
	.nav-button.active {
		color: #d6593a;
		background: #e0e0e0;
		box-shadow: inset -5px -5px 8px #a6a6a6, inset 5px 5px 8px #ffffff;
	}
	.nav-button.active.home {
		color: black;
	}
</style>