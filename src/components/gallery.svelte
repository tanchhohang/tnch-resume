<script>
    import { each } from "svelte/internal";
    import { useLazyImage as lazyImage } from "svelte-lazy-image";
    let images = []
    for(let i = 28; i >= 1; i--) {
        images.push(i);
    };
</script>

<div class="image-gallery">
    {#each images as image}
        <figure class = 'gallery_item gallery_item{image}' >
            <img src="./img/image ({image}).jpg" class = "gallery_image" alt="Image {image}" use:lazyImage />
        </figure>
    {/each}
</div>

<style>
    .image-gallery {
        margin: 10px;
        padding: 0.5em;
        gap: 0.5em;
    }

    .gallery_item {
        padding: 0px;
        margin: 0px 0px 10px 0px;
        border: 0px;
    }
    .gallery_image{
        display: block;
        width: 100%;
        border-radius: 4px;
        box-shadow: 2px 2px 5px rgba(#000, .7);
        object-fit:contain;
    }

    .gallery_item4 {
        grid-column: span 3;
    }

    @media screen and (min-device-width: 640px) {
        .image-gallery {
            display: columns;
            columns: 3;
        }

        @supports(grid-template-rows: masonry) {
            .image-gallery {
                display: grid;
                grid-template-columns: repeat(autofit, minmax(250px, 1fr));
                grid-template-rows: masonry;
                align-items: stretch;
                justify-content: center;
                grid-gap: 0.5em;
                padding: 0.5em;
            }

            .image-gallery > * {
                margin: 0px;
            }
        }
    }
</style>
