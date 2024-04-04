<script lang="ts">
    let line1: HTMLElement
    let line2: HTMLElement
    let line3: HTMLElement
    let line4: HTMLElement
    let line5: HTMLElement

</script>

<div class="container">
    <div class="inline" id="line-1">
        <span class="left">KEVIN SHAN</span>
        <span class="right">*</span>
    </div>
    <div class="inline" id="line-2">
        <span class="left">FULL STACK</span>
        <span class="right">DEV + DESIGN</span>
    </div>
    <div class="inline" id="line-3">
        <span class="left">ANDOVER</span>
        <span class="right">AMHERST</span>
    </div>
    <div class="inline space" id="line-4"></div>
    <div class="inline" id="line-5">
        <span class="left"><a href="/info">INFO</a></span>
        <span class="right"><a href="/contact">CONTACT</a></span>
    </div>
</div>

<style>
    .container {
        width: 500px;
        height: fit-content;
        display: block;
    }

    .space {
        height: 1em;
    }

    .left {
        
    }
</style>