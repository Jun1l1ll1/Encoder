<script>
    import { page } from '$app/stores';

    import Icons from "$lib/components/Icons.svelte";
    
</script>

<div class="outer bc_gray">
    <div class="grid">
        <div style="height: 100px;" class="bc_dark_gray"></div>

        <a href="/" class="element"><Icons cypher="" path={$page.url.pathname}/></a>
        <a href="/binary" class="element"><Icons cypher="binary" path={$page.url.pathname}/></a>
        <a href="/morse" class="element"><Icons cypher="morse" path={$page.url.pathname}/></a>
        <a href="/caesar" class="element"><Icons cypher="caesar" path={$page.url.pathname}/></a>
    </div>
</div>

<style>

    .grid {
        display: grid;
        grid-template-columns: auto;
    }

    .outer {
        width: 75px;
        height: 100vh;
    }

    .element {
        margin-top: 10px;
        width: 100%;
        aspect-ratio: 1/1;
        display: flex;
        justify-content: center;
        align-items: center;
    }

</style>