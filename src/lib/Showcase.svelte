<script lang="ts">
    let projects = [
        {
            text: "WORK",
            src: "mountain.jpeg",
            alt: "alt"
        },
        {
            text: "STUFF",
            src: "mountain.jpeg",
            alt: "alt"
        },
        {
            text: "STUFF",
            src: "mountain.jpeg",
            alt: "alt"
        }
    ]
</script>

<div class="space"></div>

<div class="showcase-container">
    {#each projects as project}
        <h1>{project.text}</h1>
        <div class="img-wrapper">
            <img src={project.src} alt={project.alt}>
        </div>
    {/each}
</div>

<div class="space"></div>

<svelte:window on:scroll={() => {}} />

<style>
    .showcase-container {
        position: relative;
        display: flex;
        flex-direction: column;
        align-items: center;
        row-gap: 30vh;
        z-index: 1;
    }

    .img-wrapper {
        height: 80vh;
        width: 50vw;
    }

    .space {
        height: 200vh;
    }

    h1 {
        font-family: Arial, Helvetica, sans-serif;
        font-weight: 600;
        font-size: var(--font-big);
        text-align: center;
    }

    img {
        width: inherit;
        height: inherit;

        clip-path: inset(100% 0% 0%);
        transform: translateY(-100%);

        animation: enlargen linear forwards, shrink linear forwards;
        animation-timeline: view(), view();
        animation-range-start: 10vh, 90vh;
        animation-range-end: 90vh, 170vh;
    }

    @keyframes enlargen {
        to {
            transform: translateY(0%);
            clip-path: inset(0% 0% 0%);
        }
    }

    @keyframes shrink {
        to {
            transform: translateY(100%);
            clip-path: inset(0% 0% 100%);
        }
    }
</style>