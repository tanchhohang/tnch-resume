<script>
    import { each, onMount } from "svelte/internal";
    let gallery;
    let numberOfImages = [];

    for (let i = 1; i < 9; i++) {
        numberOfImages.push(i);
    }

    onMount(async() => {
        window.onmousedown = e => {
            gallery.dataset.mousePosition = e.clientX;
        }

        window.onmousemove = e => {
            const mouseMoved = parseFloat(gallery.dataset.mousePosition) - e.clientX,
                    maxMove = window.innerWidth / 2; 
            const percentageMoved = (mouseMoved / maxMove) * 100;

            gallery.style.transform = `translate(-${percentageMoved}%, -25%)`;
        }
    });
</script>

<div bind:this = {gallery} class="image-gallery" data-mousePosition = "0px" data-mousePreviousPosition = "0px">
{#each numberOfImages as index}
    <img src="./img/image-{index}.jpg" class="galleryImage galleryImage-image{index}" alt = "Image {index}">
{/each}
</div>

<style>
    .image-gallery {
        display: flex;
        gap: 1em;
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -25%);
    }

    .image-gallery > img {
        width: 32vmin;
        height: 46vmin;
        object-fit: cover;
        object-position: 50% 50%;
    }
</style>