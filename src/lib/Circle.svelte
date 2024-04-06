<!-- <script lang="ts">
    import { spring } from "svelte/motion";

    let rotatingText: HTMLDivElement;
    let position = spring({x: 0, y: 0}, {
        stiffness: 0.05,
        damping: 0.4
    })

    function updatePosition(event: MouseEvent | WheelEvent): void {
    
        if (event.type == "wheel") position.set({x: event.clientX, y: event.pageY}, { hard: true});
        else position.set({x: event.clientX, y: event.pageY});
    }

    $: if (rotatingText != null) rotatingText.style.inset = `${$position.y - 50}px 0px 0px ${$position.x - 50}px`;
</script>

<svelte:window on:wheel={updatePosition} on:mousemove={updatePosition}/>

<div bind:this={rotatingText} class="svg-wrapper">
    <svg id="rotating-text" viewBox="0 0 200 200">
        <defs>
            <path
                id="circle"
                d="M 100, 100m -75, 0
                a 75, 75 0 1, 0 150, 0
                a 75, 75 0 1, 0 -150, 0"
            >
            </path>
        </defs>
        <text>
            <textPath alignment-baseline="inherit" xlink:href="#circle" class="circle-text">
                KEVIN SHAN WEB DEVELOPMENT AND DESIGN
            </textPath>
        </text>
    </svg>
</div>

<style>
    .circle-text {
        font-size: 1em;
        letter-spacing: 0.16em;
    }

    .svg-wrapper {
        position: absolute;
        pointer-events: none;

        width: 100px;
        height: 100px;
    }

    svg {
        width: inherit;
        height: inherit;
    }

    #rotating-text {
        animation-name: rotate-circle;
        animation-duration: 15s;
        animation-timing-function: linear;
        animation-iteration-count: infinite;
    }

    @keyframes rotate-circle {
        to {
            transform: rotate(1turn);
        }
    }
</style> -->