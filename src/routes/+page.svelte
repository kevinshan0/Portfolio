<script lang="ts">
    import Info from "$lib/Info.svelte";
</script>

<div class="info">
    <Info />
</div>

<style>
    .info {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
</style>