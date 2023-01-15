<script>
    import { each } from "svelte/internal";
    let images = []
    for(let i = 1; i <= 31; i++) {
        images.push(i);
    };
</script>

<div class="image-gallery">
    {#each images as image}
        <figure class = 'gallery_item gallery_item{image}' >
            <img src="./img/image-{image}.jpg" class = "gallery_image" alt="Image {image}">
        </figure>
    {/each}
</div>

<style>
    .image-gallery {
        margin: 10px;
        display: grid;
        grid-template-columns: repeat(3, minmax(250px, 1fr));
        gap: 5px;
        align-items: stretch;
        /* display: grid;
        grid-template-columns: repeat(12, 1fr);
        grid-auto-rows: repeat(12, 1fr);
        grid-gap: 5px; */
    }

    .gallery_item {
        padding: 0px;
        margin: 0px;
        border: 0px;
    }
    .gallery_image{
        width: 100%;
        object-fit:contain;
    }

    .gallery_item19 {
        grid-column: span 3;
    }
</style>