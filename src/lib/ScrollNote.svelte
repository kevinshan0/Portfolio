<script lang="ts">
    import { tweened } from "svelte/motion";

    let element: HTMLElement;

    let opacity = tweened(1, {
        duration: 100,
    })

    $: if (element != null) element.style.opacity = `${$opacity}`;
</script>

<svelte:window on:scroll={() => {opacity.set(0)}} />
<div bind:this={element}>
    <p>SCROLL TO EXPLORE</p>
</div>

<style>
    div {
        width: fit-content;
        height: fit-content;

        position: fixed;
        inset: 90vh 0 0 0;
        margin: auto;

        font-size: 0.2em;
    }
</style>