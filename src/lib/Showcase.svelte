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

<div class="space big"></div>

<div class="showcase-container">
    {#each projects as project}
        <div class="project">
            <h1>{project.text}</h1>
            <div class="space small"></div>
            <div class="img-wrapper"><img src={project.src} alt={project.alt}></div>
        </div>
    {/each}
</div>

<div class="space big"></div>

<svelte:window on:scroll={() => {}} />

<style>
    .showcase-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        row-gap: 30vh;

        position: relative;
        z-index: 1;
    }

    .project {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .img-wrapper {
        min-height: 80vh;
        min-width: 50vw;
        height: 80vh;
        width: 50vw;
    }

    .space.big {
        height: 200vh;
    }

    .space.small {
        height: 30vh;
    }

    h1 {
        font-family: Arial, Helvetica, sans-serif;
        font-weight: 600;
        font-size: 10em;
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