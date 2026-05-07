# Blog Template

<img width="1727" height="997" alt="Screenshot 2026-05-06 210908" src="https://github.com/user-attachments/assets/c110200f-941b-4551-990b-c3245e6f7333" />

A minimal blog template built with SvelteKit. Dark theme, sidebar navigation, searchable post list, and previous/next post navigation.

## Quick start

```sh
cd client
npm install
npm run dev
```

The dev server runs at `http://localhost:5173`.

## Making it yours

### Site name and tagline

Open `src/lib/config.js` and change the two exported values:

```js
export const SITE_NAME = 'My Blog';
export const SITE_TAGLINE = 'thoughts and writing';
```

These are used in the sidebar and home page. That's the only file you need to touch for basic branding.

### Adding a post

1. Add an entry to `src/lib/posts.json`:

```json
{
    "slug": "3",
    "title": "my new post",
    "date": "May 30, 2026"
}
```

2. Create the file `src/routes/posts/3/+page.svelte` with your content:

```svelte
<script>
import PostNav from '$lib/PostNav.svelte';
</script>

<div class="pageContainer">
    <div class="pageLeft">
        <span class="goodText">my new post</span>
        <p class="tinyText">MAY 10, 2026</p>
        <p>Your content here.</p>
    </div>
    <div class="pageRight">
        <!-- optional second column -->
    </div>
</div>

<PostNav slug="3" />
```

The `slug` in `PostNav` must match the slug in `posts.json`. The `PostNav` component automatically generates previous and next links based on the order of entries in `posts.json`.

### Changing the accent color

The accent color (used on hover states throughout the site) is `#ffb347`. To change it, search for `#ffb347` across the project and replace it with your color.

### Changing the background

Open `static/style.css`. Near the top you'll find the `html` rule with a comment explaining the options:

```css
/* background image (current default) */
html {
    background: url("./Images/74175.JPG");
    background-size: cover;
    box-shadow: inset 0 0 0 2000px rgba(0, 0, 0, 0.8);
}

/* or a solid color */
html {
    background-color: #1a1a1a;
}
```

Place any background image in `static/Images/` and reference it with `./Images/filename`.

### Changing the heading font

The large display text uses the `.goodText` class in `static/style.css`. To use a different font, add an `@font-face` declaration pointing to your font file and update the `font-family` on `.goodText`:

```css
@font-face {
    font-family: MyFont;
    src: url("/fonts/fonts/MyFont.ttf");
}

.goodText {
    font-family: 'MyFont', sans-serif;
    font-size: 75px;
}
```

Place font files in `static/fonts/fonts/`.

### Changing the body font

The body uses Comfortaa. To change it, update the `font-family` on `body` in `static/style.css` and add the corresponding `@font-face` if needed.

### About page

Edit `src/routes/about/+page.svelte` directly. It's plain HTML, replace the placeholder text with your own.

## Project structure

```
src/
  lib/
    config.js         <- site name and tagline
    posts.json        <- list of all posts
    PostNav.svelte    <- previous/next post links
    ZoomImg.svelte    <- click-to-zoom image component
  routes/
    +layout.svelte    <- sidebar and page shell
    +page.svelte      <- home page
    about/
      +page.svelte    <- about page
    posts/
      +page.svelte    <- searchable post list
      1/+page.svelte  <- individual post
      2/+page.svelte  <- individual post
static/
  style.css           <- global styles, fonts, colors
  fonts/              <- font files
```

## Building for production

```sh
npm run build
npm run preview
```

To deploy, install an adapter for your target platform. See the [SvelteKit adapter docs](https://svelte.dev/docs/kit/adapters).
