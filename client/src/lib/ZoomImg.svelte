<script>
    import 'photoswipe/style.css';
    import PhotoSwipe from 'photoswipe';

    let { src, alt, style: inlineStyle = '', class: className = '', ...rest } = $props();

    let imgEl;

    function open() {
        const rect = imgEl.getBoundingClientRect();

        const pswp = new PhotoSwipe({
            dataSource: [{
                src,
                width: imgEl.naturalWidth,
                height: imgEl.naturalHeight,
                alt,
                msrc: src
            }],
            index: 0,
            bgOpacity: 0.9,
            clickToCloseNonZoomable: false,
            secondaryZoomLevel: 2.5,
            maxZoomLevel: 4,
            showHideAnimationType: 'zoom',
            getThumbBoundsFn: () => ({
                x: rect.left,
                y: rect.top + window.scrollY,
                w: rect.width
            })
        });
        pswp.init();
    }
</script>

<img
    bind:this={imgEl}
    {src}
    {alt}
    style={inlineStyle}
    class={className}
    onclick={open}
    style:cursor="zoom-in"
    {...rest}
/>
