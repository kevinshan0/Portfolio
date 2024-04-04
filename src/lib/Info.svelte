<script lang="ts">
    let infoAnchor: HTMLAnchorElement;
    let contactAnchor: HTMLAnchorElement;

    function hoverAction(event: Event) {
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
            console.log()
        }

        let interval = setInterval(shuffle, 50);
    }
</script>

<div class="container">
    <div class="inline">
        <div>KEVIN SHAN</div>
        <div>*</div>
    </div>
    <div class="inline">
        <div>FULL STACK</div>
        <div>DEV + DESIGN</div>
    </div>
    <div class="inline">
        <div>ANDOVER</div>
        <div>AMHERST</div>
    </div>
    <div class="inline space"></div>
    <div class="inline">
        <div><a on:mouseenter={hoverAction} bind:this={infoAnchor} href="/info">INFO</a></div>
        <div><a on:mouseenter={hoverAction} bind:this={contactAnchor} href="/contact">CONTACT</a></div>
    </div>
</div>

<style>
    .container {
        width: 300px;
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
</style>