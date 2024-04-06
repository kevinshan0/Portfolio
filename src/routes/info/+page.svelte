<script lang="ts">
    import { onMount } from "svelte";

    let homeAnchor: HTMLAnchorElement;
    let allTextDivs: Array<HTMLElement>;

    async function onMountAnimation(): Promise<void> {
        allTextDivs = Array.from(document.querySelectorAll(".line-section"));
        let allTextArray = allTextDivs.map(element => element.innerText);
        
        allTextDivs.forEach(element => element.innerText = "");

        for (const [index, element] of allTextDivs.entries()) {
            await loadText(element, index);
        }

        function loadText(element: HTMLElement, index: number): Promise<void> {
            return new Promise((resolve) => {
                setTimeout(resolve, 10);

                let innerTextArray = allTextArray[index];
                let replacement = "";
                let counter = 0;

                function shuffle(): void {
                    element.innerText = replacement;
                    replacement += innerTextArray[counter];
                    counter++;

                    if (counter == innerTextArray.length + 1) {
                        clearInterval(interval);
                    }
                }

                let interval = setInterval(shuffle, 50);
            })
        }
    }
        
    function hoverAction(event: Event): void {
        let element = event.target as HTMLAnchorElement;
        let text = element.innerText;
        let counter = 0;

        function shuffle(): void {
            let newText = "";
        
            if (element === homeAnchor) {
                switch (counter) {
                    case 0:
                        newText = "OMEH";
                        break;
                    case 1:
                        newText = "HEMO";
                        break;
                    case 2:
                        newText = "HOEM";
                        break;
                    case 3:
                        newText = "HOME";
                        break;
                }
            }

            element.innerText = newText;
            counter++;

            if (counter == text.length) clearInterval(interval);
        }

        let interval = setInterval(shuffle, 50);
    }

    onMount(onMountAnimation);
</script>

<div class="container">
    <div class="section">
        <div class="line"><span class="line-section">I AM A SENIOR </span><span class="line-section">AT ANDOVER HIGH SCHOOL</span></div>
        <div class="line"><span class="line-section">(AT LEAST UNTIL </span><span class="line-section">THE END OF MAY).</span></div>
    </div>
    <div class="section">
        <div class="line"><span class="line-section">I WILL BE ATTENDING </span><span class="line-section">UMASS AMHERST</span></div>
        <div class="line"><span class="line-section">FOR COMPUTER </span><span class="line-section">SCIENCE AND AM AN</span></div>
        <div class="line"><span class="line-section">ASPIRING WEB DEV</span><span class="line-section">ELOPER AND DESIGNER</span></div>
        <div class="line"><span class="line-section">(AS YOU CAN TELL).</span></div>
    </div>
    <a on:mouseenter={hoverAction} bind:this={homeAnchor} href="/" class="small">HOME</a>
</div>

<style>
    .container {
        position: fixed;
        inset: 0;
        margin: auto;

        width: 80vw;
        height: fit-content;

        display: flex;
        flex-direction: column;
        align-items: center;
        gap: var(--gap);
    }

    .section {
        width: inherit;
        height: fit-content;

        display: flex;
        flex-direction: column;
        gap: 0.5em;
    }

    .line {
        width: inherit;
        height: fit-content;
        
        font-size: var(--font-medium);
        text-align-last: justify;
    }

    .small {
        font-size: var(--font-small);
    }
</style>