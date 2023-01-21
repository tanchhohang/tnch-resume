<script>
    import { each, onMount } from "svelte/internal";
    import { useLazyImage as lazyImage } from "svelte-lazy-image";
    let gallery;
    let images = {};
    let numberOfImages = [];

    for (let i = 1; i < 9; i++) {
        numberOfImages.push(i);
    }

    onMount(async() => {
        window.onmousedown = e => {
            gallery.dataset.mouseposition = e.clientX;
        }

        window.onmouseup = e => {
            gallery.dataset.mouseposition = "0";
            gallery.dataset.mouseprevpercentage = gallery.dataset.prevpercentage;
        }

        window.onmousemove = e => {

            if (gallery.dataset.mouseposition === "0") return;

            const mouseMoved = ((parseFloat(gallery.dataset.mouseposition) - e.clientX)*200)/window.innerWidth;
            const percentageToMove = mouseMoved + parseFloat(gallery.dataset.mouseprevpercentage) < 0 ? 0: mouseMoved + parseFloat(gallery.dataset.mouseprevpercentage) > 100 ? 100: mouseMoved + parseFloat(gallery.dataset.mouseprevpercentage) ;
            console.table(gallery.dataset);
            gallery.dataset.prevpercentage = percentageToMove;
            gallery.animate({
                transform:` translate(-${parseFloat(percentageToMove)}%, -50%)`
            }, {duration: 600, fill: "forwards"});
            images.values().forEach(image => {
                image.animate({
                    objectPosition: `${percentageToMove}% center`
                }, {duration: 600, fill: "forwards"});
            });
        }
    });
</script>

<div bind:this = {gallery} class="image-gallery" data-mouseposition = '0' data-mouseprevpercentage = '0' data-prevpercentage = '0'>
{#each numberOfImages as index}
    <img bind:this = {images[`image${index}`]} src="./img/image-{index}.jpg" class="galleryImage galleryImage-image{index}" alt = "Image {index}" draggable="false" use:lazyImage />
{/each}
</div>

<style>
    .image-gallery {
        display: flex;
        gap: 4vmin ;
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(0%, -50%);
    }
    
    .image-gallery > img {
        user-select: none;
        width: 32vmin;
        height: 44vmin;
        object-fit:cover;
        object-position: 100% center;
    }
</style>