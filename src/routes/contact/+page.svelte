<script lang="ts">
    import { base } from '$app/paths';

    let instagramAnchor: HTMLAnchorElement;
    let githubAnchor: HTMLAnchorElement;
    let homeAnchor: HTMLAnchorElement;

    function hoverAction(event: Event): void {
        let element = event.target as HTMLAnchorElement;
        let text = element.innerText;
        let counter = 0;

        function shuffle(): void {
            let newText = "";

            if (element === instagramAnchor) {
                switch (counter) {
                    case 0:
                        newText = "GMNRATSAI";
                        break;
                    case 1:
                        newText = "IAGNSMTRA";
                        break;
                    case 2:
                        newText = "INATMSAGR";
                        break;
                    case 3:
                        newText = "INSARTMAG";
                        break;
                    case 4:
                        newText = "INSTGMAAR";
                        break;
                    case 5:
                        newText = "INSTAMGRA";
                        break;
                    case 6:
                        newText = "INSTAGMAR";
                        break;
                    case 7:
                        newText = "INSTAGRMA";
                        break;
                    case 8:
                        newText = "INSTAGRAM";
                        break;
                }
            }

            if (element === githubAnchor) {
                switch (counter) {
                    case 0:
                        newText = "TIUBHG";
                        break;
                    case 1:
                        newText = "GUHITB";
                        break;
                    case 2:
                        newText = "GIUBHT";
                        break;
                    case 3:
                        newText = "GITBUH";
                        break;
                    case 4:
                        newText = "GITHBU";
                        break;
                    case 5:
                        newText = "GITHUB";
                        break;
                }
            }

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
</script>

<div class="container">
    <a on:mouseenter={hoverAction} bind:this={instagramAnchor} href="https://www.instagram.com/kevinshan0/?hl=en" class="big">INSTAGRAM</a>
    <a on:mouseenter={hoverAction} bind:this={githubAnchor} href="https://github.com/kshan2024" class="big">GITHUB</a>
    <a on:mouseenter={hoverAction} bind:this={homeAnchor} href="{base}/" class="small">HOME</a>
</div>

<style>
    .container {
        position: fixed;
        inset: 0;
        margin: auto;
        width: fit-content;
        height: fit-content;

        display: flex;
        flex-direction: column;
        align-items: center;
        gap: calc( 0.2 * var(--gap));
    }

    .big {
        font-size: var(--font-big);
    }

    .small {
        font-size: var(--font-small);
    }
</style>