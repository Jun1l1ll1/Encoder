<script>

    import Navbar from "$lib/components/Navbar.svelte";

</script>

<div style="display: flex;">
    <Navbar/> 

    <div style="padding: 25px;">
        <slot/>
    </div>

</div>

