<script>

    import { navigating } from '$app/stores';
    import Navbar from "$lib/components/Navbar.svelte";

</script>

<div style="display: flex;">
    {#key $navigating}
    <Navbar/> 
    {/key}

    <div style="width:100%;">
        <slot/>
    </div>

</div>

