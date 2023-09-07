
<div class="outer bc_gray">
    <div class="grid">
        <div style="height: 100px;" class="bc_dark_gray"></div>

        <a href="/" class="element">home</a>
        <a href="/binary" class="element">binary</a>
        <a href="/morse" class="element">morse</a>
        <a href="/ceasar" class="element">ceasar</a>
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
        width: 100%;
        aspect-ratio: 1/1;
        display: flex;
        justify-content: center;
        align-items: center;
    }

</style>