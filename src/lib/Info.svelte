<script lang="ts">
    import { onMount } from "svelte";

    let allTextDivs: NodeListOf<HTMLElement>;
    let infoAnchor: HTMLAnchorElement;
    let contactAnchor: HTMLAnchorElement;

    async function onMountAnimation(): Promise<void> {
        allTextDivs = document.querySelectorAll(".text");
        let allTextArray = Array.from(allTextDivs).map((element) => element.innerText);
        
        allTextDivs.forEach(element => element.innerText = "");

        for (const [index, element] of allTextDivs.entries()) {
            await loadText(element, index);
        }

        function loadText(element: HTMLElement, index: number): Promise<void> {
            return new Promise((resolve) => {
                setTimeout(resolve, 120);

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
        let text = (element === infoAnchor) ? "INFO" : "CONTACT";
        let counter = 0;

        function shuffle(): void {
            let unchanging = text.substring(0, counter);
            let changing: string;

            if (element === contactAnchor) {
                switch (counter) {
                    case 0:
                        changing = "ONCTCAT";
                        break;
                    case 1:
                        changing = "TAOCTN";
                        break;
                    case 2:
                        changing = "ATNTC";
                        break;
                    case 3:
                        changing = "ATTC";
                        break;
                    case 4:
                        changing = "CAT";
                        break;
                    case 5:
                        changing = "TC";
                        break;
                    case 6:
                        changing = "T";
                        break;
                    default:
                        changing = "";
                        break;
                }

                let result = unchanging + changing;
                contactAnchor.innerText = result;
            }
            
            if (element === infoAnchor) {
                switch (counter) {
                    case 0:
                        changing = "OFIN";
                        break;
                    case 1:
                        changing = "FNO";
                        break;
                    case 2:
                        changing = "OF";
                        break;
                    case 3:
                        changing = "F";
                        break;
                    default:
                        changing = "";
                        break;
                }

                let result = unchanging + changing;
                infoAnchor.innerText = result;
            }

            counter++;

            if (counter == text.length + 1) clearInterval(interval);
        }

        let interval = setInterval(shuffle, 50);
    }

    onMount(onMountAnimation);
</script>

<div class="container">
    <div class="inline">
        <div class="text">KEVIN SHAN</div>
        <div class="text">THE CREATOR</div>
    </div>
    <div class="inline">
        <div class="text">DEVELOPMENT</div>
        <div class="text">+</div>
        <div class="text">DESIGN</div>
    </div>
    <div class="inline">
        <div class="text">ANDOVER</div>
        <div class="text">AMHERST</div>
    </div>
    <div class="inline space"></div>
    <div class="inline">
        <div><a on:mouseenter={hoverAction} bind:this={infoAnchor} href="/info" class="text">INFO</a></div>
        <div><a on:mouseenter={hoverAction} bind:this={contactAnchor} href="/contact" class="text">CONTACT</a></div>
    </div>
</div>

<style>
    .container {
        width: 400px;
        height: fit-content;
        display: block;
    }

    .inline {
        display: flex;
        justify-content: space-between;
    }

    .space {
        height: 1em;
    }

    a {
        text-decoration: none;
        color: black;
    }
</style>