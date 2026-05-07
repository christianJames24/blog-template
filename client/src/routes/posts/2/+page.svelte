<script>
import PostNav from '$lib/PostNav.svelte';
import ShapeOutsideFix from '$lib/ShapeOutsideFix.svelte';
import ZoomImg from '$lib/ZoomImg.svelte';
</script>

<ShapeOutsideFix />

<div class="pageContainer">
	<div class="pageLeft">
		<span class="goodText">a second post</span>
		<p class="tinyText">MAY 5, 2026</p>
		<ZoomImg src="/Images/downloads-42.png" alt="example" style="float: left; width: 200px; margin: 0 1.5rem 1rem 0; shape-outside: url(/Images/downloads-42.png);" />
		<p>
			This is a second example post to show how the posts list and navigation work with more than one entry.
		</p>
		<p>
			When you're ready to replace these example posts with real ones, update <code>src/lib/posts.json</code> and swap out the content in each post's <code>+page.svelte</code> file.
		</p>
	</div>
	<div class="pageRight">
	</div>
</div>

<PostNav slug="2" />

<style>
code {
	background: #333;
	padding: 0.1em 0.4em;
	border-radius: 3px;
	font-size: 0.85em;
}
</style>
