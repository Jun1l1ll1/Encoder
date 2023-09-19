<script>
    export let right = true;
    export let color = "white";
</script>

<style>
    .arrow {
        width: 30px;
        margin-top: 5px;
    }

    .arrow_rect {
        stroke-width: 0px;
    }
</style>

{#if right}
    <svg id="arr_right" style="fill: {color};" class="arrow" data-name="Arrow Right" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 534.56 346.68">
        <rect class="arrow_rect" y="144.41" width="526" height="54" rx="27" ry="27"/>
        <rect class="arrow_rect" x="305.66" y="72.27" width="258.42" height="54" rx="27" ry="27" transform="translate(197.57 -278.42) rotate(45)"/>
        <rect class="arrow_rect" x="306.08" y="220.41" width="258.42" height="54" rx="27" ry="27" transform="translate(-47.45 380.26) rotate(-45)"/>
    </svg>
{:else}
    <svg id="arr_left" style="fill: {color};" class="arrow" data-name="Arrow Left" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 534.56 346.68">
        <rect class="arrow_rect" x="8.56" y="144.41" width="526" height="54" rx="27" ry="27" transform="translate(543.12 342.82) rotate(180)"/>
        <rect class="arrow_rect" x="-29.52" y="72.27" width="258.42" height="54" rx="27" ry="27" transform="translate(-41 99.57) rotate(-45)"/>
        <rect class="arrow_rect" x="72.27" y="118.2" width="54" height="258.42" rx="27" ry="27" transform="translate(-145.87 142.66) rotate(-45)"/>
    </svg>
{/if}
