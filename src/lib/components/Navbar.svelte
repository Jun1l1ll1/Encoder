<script>
    import { page } from '$app/stores';

    import Icons from "$lib/components/Icons.svelte";
    
</script>

<div class="outer">
    <div class="follow bc_gray">
        <div class="grid">
            <div style="height: 100px;" class="bc_dark_gray"></div>
            
            <a href="/" class="element"><Icons cypher="" path={$page.url.pathname}/></a>
            <a href="/binary" class="element"><Icons cypher="binary" path={$page.url.pathname}/></a>
            <a href="/morse" class="element"><Icons cypher="morse" path={$page.url.pathname}/></a>
            <a href="/caesar" class="element"><Icons cypher="caesar" path={$page.url.pathname}/></a>
            <a href="/a1z26" class="element"><Icons cypher="a1z26" path={$page.url.pathname}/></a>
            <a href="/atbash" class="element"><Icons cypher="atbash" path={$page.url.pathname}/></a>
        </div>
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
    .follow {
        position: fixed;
        width: 75px;
        height: 100vh;
        z-index: 10;
    }

    .element {
        margin-top: 10px;
        width: 100%;
        aspect-ratio: 3/2;
        display: flex;
        justify-content: center;
        align-items: center;
    }

</style>