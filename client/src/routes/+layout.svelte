<script>
import { onMount } from 'svelte';
import favicon from '$lib/assets/favicon.svg';
import posts from '$lib/posts.json';
import { SITE_NAME, SITE_TAGLINE } from '$lib/config.js';

const recentPosts = [...posts].sort((a, b) => new Date(b.date) - new Date(a.date)).slice(0, 5);
let sidebarOpen = $state(false);

onMount(() => {
	if (window.innerWidth >= 768) sidebarOpen = true;
});

function toggleSidebar() {
	sidebarOpen = !sidebarOpen;
}

function closeSidebarOnMobile() {
	if (window.innerWidth < 768) sidebarOpen = false;
}
</script>


<svelte:head>
    <link rel="icon" href={favicon} />
</svelte:head>



<div class="layout">
	<button class="backdrop" class:visible={sidebarOpen} onclick={toggleSidebar} aria-label="Close sidebar"></button>
	<div class="sidebar-wrapper" class:open={sidebarOpen}>
		<nav class="sidebar">
			<button class="close-btn" onclick={toggleSidebar} aria-label="Close sidebar">X</button>
			<div class="sidebar-brand">
				<h2>{SITE_NAME}</h2>
				<p class="sidebar-tagline">{SITE_TAGLINE}</p>
			</div>
			<div class="sidebar-section">
				<span class="section-label">navigate</span>
				<ul>
					<li><a class="whiteHover" href="/" onclick={closeSidebarOnMobile}>home</a></li>
					<li><a class="whiteHover" href="/posts" onclick={closeSidebarOnMobile}>posts</a></li>
					<li><a class="whiteHover" href="/about" onclick={closeSidebarOnMobile}>about</a></li>
				</ul>
			</div>
			<div class="sidebar-section">
				<span class="section-label">recent posts</span>
				<ul>
					{#each recentPosts as post}
						<li><a class="whiteHover" href="/posts/{post.slug}" onclick={closeSidebarOnMobile}>{post.title}</a></li>
					{/each}
				</ul>
			</div>
		</nav>
	</div>
	<main class="content" class:sidebar-closed={!sidebarOpen}>
		<button class="open-btn" class:hidden={sidebarOpen} onclick={toggleSidebar} aria-label="Open sidebar">☰</button>
		<slot />
	</main>
</div>

<style>
.layout {
	display: flex;
	min-height: 100vh;
}

.sidebar-wrapper {
	width: 0;
	overflow: hidden;
	flex-shrink: 0;
	transition: width 0.25s ease;
}
.sidebar-wrapper.open {
	width: 225px;
}


.sidebar {
	width: 225px;
	box-sizing: border-box;
	height: 100%;
	background: #222;
	color: #fff;
	padding: 2rem 1rem;
	box-shadow: 2px 0 8px rgba(0,0,0,0.05);
	position: relative;
	z-index: 2;
}
.close-btn {
	position: absolute;
	top: 1rem;
	right: 1rem;
	background: none;
	border: none;
	color: #fff;
	font-size: 1.5rem;
	cursor: pointer;
	padding: 0.2em 0.5em;
}
.open-btn {
	position: absolute;
	top: 1.5rem;
	left: 1.5rem;
	background: #222;
	color: #fff;
	border: none;
	font-size: 2rem;
	cursor: pointer;
	border-radius: 4px;
	z-index: 3;
	padding: 0.2em 0.6em;
	box-shadow: 2px 2px 8px rgba(0,0,0,0.08);
	transition: opacity 0.2s ease;
}

.open-btn:hover{
    color: #ffb347;
}
.close-btn:hover{
	color: #ffb347;
}

.open-btn.hidden {
	opacity: 0;
	pointer-events: none;
}
.sidebar-brand {
	margin-bottom: 2rem;
	padding-bottom: 1.2rem;
	border-bottom: 1px solid #333;
}
.sidebar h2 {
	margin: 0 0 0.2rem;
	font-size: 1.5rem;
}
.sidebar-tagline {
	margin: 0;
	font-size: 0.78rem;
	color: #777777;
}
.sidebar-section {
	margin-bottom: 1.6rem;
}
.section-label {
	display: block;
	font-size: 0.7rem;
	text-transform: uppercase;
	letter-spacing: 0.12em;
	color: #a5a5a5;
	margin-bottom: 0.6rem;
}
.sidebar ul {
	list-style: none;
	padding: 0;
}
.sidebar li {
	margin-bottom: 1.2rem;
}
.sidebar a {
	font-size: 1.1rem;
}
.content {
	flex: 1;
	padding: 2rem;
	padding-top: 2rem;
	position: relative;
	transition: padding-top 0.25s ease;
}
.content.sidebar-closed {
	padding-top: 5rem;
}
.backdrop {
	display: none;
	opacity: 0;
	transition: opacity 0.25s ease;
	pointer-events: none;
}
@media (max-width: 767px) {
	.sidebar-wrapper {
		width: 0;
		overflow: visible;
	}
	.sidebar-wrapper.open {
		width: 0;
	}
	.sidebar {
		width: 75%;
		position: fixed;
		top: 0;
		left: 0;
		height: 100vh;
		z-index: 100;
		transform: translateX(-100%);
		transition: transform 0.25s ease;
	}
	.sidebar-wrapper.open .sidebar {
		transform: translateX(0);
	}
	.open-btn {
		position: fixed;
		top: 1rem;
		left: 1rem;
		z-index: 50;
	}
	.backdrop {
		display: block;
		position: fixed;
		inset: 0;
		background: rgba(0, 0, 0, 0.5);
		z-index: 99;
		border: none;
		cursor: pointer;
	}
	.backdrop.visible {
		opacity: 1;
		pointer-events: auto;
	}
}
</style>
