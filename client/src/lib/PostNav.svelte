<script>
import posts from '$lib/posts.json';

let { slug } = $props();

const index = posts.findIndex(p => p.slug === slug);
const prev = posts[index - 1] ?? null;
const next = posts[index + 1] ?? null;
</script>

{#if prev || next}
	<nav class="post-nav">
		<div class="post-nav-side">
			{#if prev}
				<a href="/posts/{prev.slug}">← {prev.title}</a>
			{/if}
		</div>
		<div class="post-nav-side right">
			{#if next}
				<a href="/posts/{next.slug}">{next.title} →</a>
			{/if}
		</div>
	</nav>
{/if}

<style>
.post-nav {
	display: flex;
	justify-content: space-between;
	padding: 1.5rem 0 0.5rem;
	margin-top: 2rem;
	border-top: 1px solid #333;
	gap: 1rem;
}
.post-nav-side {
	flex: 1;
}
.post-nav-side.right {
	text-align: right;
}
.post-nav a {
	color: #c4c4c4;
	text-decoration: none;
	font-size: 0.95rem;
	transition: color 0.2s;
}
.post-nav a:hover {
	color: #ffb347;
}
</style>
