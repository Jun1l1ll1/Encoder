<script>

    import Navbar from "$lib/components/Navbar.svelte";

</script>

<div style="display: flex;">
    <Navbar/> 

    <div style="width:100%;">
        <slot/>
    </div>

</div>

