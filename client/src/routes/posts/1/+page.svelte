<script>
import PostNav from '$lib/PostNav.svelte';
import ShapeOutsideFix from '$lib/ShapeOutsideFix.svelte';
import ZoomImg from '$lib/ZoomImg.svelte';
</script>

<ShapeOutsideFix />

<div class="pageContainer">
	<div class="pageLeft">
		<span class="goodText">hello world</span>
		<p class="tinyText">MAY 6, 2026</p>
		<ZoomImg src="/Images/9fb84854c6bf0e1c3a5d82548db47146.jpg" alt="example" style="float: left; width: 300px; margin-right: 15px; margin-bottom: 15px;" />
		<p>
			This is the first example post. Replace this content with your own writing.
		</p>
		<p>
			Each post lives in its own folder under <code>src/routes/posts/</code>. The folder name becomes the URL slug. To add a new post, create a new folder with a <code>+page.svelte</code> file inside it, then add an entry to <code>src/lib/posts.json</code>.
		</p>
		<p>
			You can write whatever you want here. Long paragraphs, short ones, images, links. The layout handles the rest.
		</p>
		<p>
			Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. In enim justo, rhoncus ut, imperdiet a, venenatis vitae, justo. Nullam dictum felis eu pede mollis pretium. Integer tincidunt. Cras dapibus. Vivamus elementum semper nisi. Aenean vulputate eleifend tellus. Aenean leo ligula, porttitor eu, consequat vitae, eleifend ac, enim. Aliquam lorem ante, dapibus in, viverra quis, feugiat a,
		</p>
	</div>
	<div class="pageRight">
		<ZoomImg src="/Images/star-7685389_1280.png" alt="example" style="float: right; width: 400px; shape-outside: url(/Images/star-7685389_1280.png);" />
		<p>
			The two-column layout is optional. If you only want one column, just leave <code>pageRight</code> empty or remove it entirely and adjust the CSS in <code>style.css</code>.
		</p>
		<p>
			The <code>PostNav</code> component below automatically generates previous and next links based on the order of posts in <code>posts.json</code>.
		</p>

		<p>
			Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. In enim justo, rhoncus ut, imperdiet a, venenatis vitae, justo. Nullam dictum felis eu pede mollis pretium. Integer tincidunt. Cras dapibus. Vivamus elementum semper nisi. Aenean vulputate eleifend tellus. Aenean leo ligula, porttitor eu, consequat vitae, eleifend ac, enim. Aliquam lorem ante, dapibus in, viverra quis, feugiat a, 
		</p>
		<p>
			Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium q
		</p>

		<p>
			Hello this paragraph will contain an <a href="https://bulbapedia.bulbagarden.net/wiki/Piplup_(Pok%C3%A9mon)" target="_blank">example of a URL</a>! This will contain the url to the Bulbapedia page for Piplup, the penguin Pokemon.
		</p>
	</div>
</div>

<PostNav slug="1" />

<style>
code {
	background: #333;
	padding: 0.1em 0.4em;
	border-radius: 3px;
	font-size: 0.85em;
}
</style>
