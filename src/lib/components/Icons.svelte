<script>
    export let cypher = "binary";
    export let path = "/";
    export let color = "white"
    export let is_static = false;

    let show_icon = false; // Hvis vi en gang vil ha ikoner så er det i koden

    let fill_color = path == "/"+cypher ? "#00FF62" : color;
    
</script>

<style>

    .icon {
        fill: var(--color);
        height: 60%;
        transition: .25s;
    }
    .icon_hover:hover {
        fill: #00FF62;
    }
</style>

{#if show_icon}
    {#if cypher == "binary"}
        <svg style="--color: {fill_color}" class="icon {is_static ? "" : "icon_hover"}" id="binary" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 78 100">
            <path class="cls-1" d="m3.28,16.51L18.32,2.64c.79-.73,1.83-1.14,2.91-1.14h5.35c2.08,0,3.77,1.69,3.77,3.77v38.97c0,2.08-1.69,3.77-3.77,3.77h-3.52c-2.08,0-3.77-1.69-3.77-3.77v-26.55c0-1.08-1.31-1.62-2.07-.86l-6.92,6.92c-1.47,1.47-3.86,1.47-5.33,0l-1.8-1.8c-1.51-1.51-1.46-3.98.11-5.43Z"/>
            <path class="cls-1" d="m42.3,11.51v27.15c0,5.16,4.18,9.34,9.34,9.34h15.02c5.16,0,9.34-4.18,9.34-9.34V11.51c0-5.16-4.18-9.34-9.34-9.34h-15.02c-5.16,0-9.34,4.18-9.34,9.34Zm19.83,25.7h-5.97c-1.7,0-3.08-1.38-3.08-3.08v-18.1c0-1.7,1.38-3.08,3.08-3.08h5.97c1.7,0,3.08,1.38,3.08,3.08v18.1c0,1.7-1.38,3.08-3.08,3.08Z"/>
            <path class="cls-1" d="m1.86,61.53v27.15c0,5.16,4.18,9.34,9.34,9.34h15.02c5.16,0,9.34-4.18,9.34-9.34v-27.15c0-5.16-4.18-9.34-9.34-9.34h-15.02c-5.16,0-9.34,4.18-9.34,9.34Zm19.83,25.7h-5.97c-1.7,0-3.08-1.38-3.08-3.08v-18.1c0-1.7,1.38-3.08,3.08-3.08h5.97c1.7,0,3.08,1.38,3.08,3.08v18.1c0,1.7-1.38,3.08-3.08,3.08Z"/>
            <path class="cls-1" d="m43.99,66.86l15.03-13.88c.79-.73,1.83-1.14,2.91-1.14h5.35c2.08,0,3.77,1.69,3.77,3.77v38.97c0,2.08-1.69,3.77-3.77,3.77h-3.52c-2.08,0-3.77-1.69-3.77-3.77v-26.55c0-1.08-1.31-1.62-2.07-.86l-6.92,6.92c-1.47,1.47-3.86,1.47-5.33,0l-1.8-1.8c-1.51-1.51-1.46-3.98.11-5.43Z"/>
        </svg>
    {:else if cypher == ""}
        <svg style="--color: {fill_color}" class="icon {is_static ? "" : "icon_hover"}" id="home" data-name="Layer 2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 97.37 96.85">
            <path class="cls-1" d="m95.27,36.64L51.08,12.54c-1.19-.65-2.62-.65-3.82-.02L2.12,36.66c-1.92,1.03-2.67,3.39-1.7,5.34l1.45,2.91c.99,1.98,3.41,2.79,5.39,1.8l5.19-2.59c.56-.28,1.22.13,1.22.75v33.62c0,2.22,1.8,4.02,4.02,4.02h61.96c2.22,0,4.02-1.8,4.02-4.02v-33.62c0-.63.66-1.03,1.22-.75l5.19,2.59c1.98.99,4.4.19,5.39-1.8l1.47-2.94c.97-1.93.23-4.29-1.67-5.32Zm-22.6,33.63c0,.68-.55,1.23-1.23,1.23H26.91c-.68,0-1.23-.55-1.23-1.23v-31.63c0-.46.25-.87.66-1.09l22.25-11.72c.37-.2.82-.19,1.18.02l22.29,12.58c.39.22.63.63.63,1.07v30.77Z"/>
        </svg>
    {:else if cypher == "morse"}
        <svg style="--color: {fill_color}" class="icon {is_static ? "" : "icon_hover"}" id="morse" data-name="Layer 3" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
            <rect class="cls-1" x="8" y="20" width="36" height="11" rx="4.62" ry="4.62"/>
            <rect class="cls-1" x="58" y="20" width="11" height="11" rx="4.62" ry="4.62"/>
            <rect class="cls-1" x="8" y="47" width="11" height="11" rx="4.62" ry="4.62"/>
            <rect class="cls-1" x="33" y="73" width="11" height="11" rx="4.62" ry="4.62"/>
            <rect class="cls-1" x="8" y="73" width="11" height="11" rx="4.62" ry="4.62"/>
            <rect class="cls-1" x="33" y="47" width="36" height="11" rx="4.62" ry="4.62"/>
            <rect class="cls-1" x="83" y="20" width="11" height="11" rx="4.62" ry="4.62"/>
        </svg>
    {:else if cypher == "caesar"}
        <svg style="--color: {fill_color}" class="icon {is_static ? "" : "icon_hover"}" id="caesar" data-name="Layer 4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
            <path class="cls-1" d="m49,0C21.94,0,0,21.94,0,49s21.94,49,49,49,49-21.94,49-49S76.06,0,49,0Zm0,86.53c-20.73,0-37.53-16.8-37.53-37.53S28.27,11.47,49,11.47s37.53,16.8,37.53,37.53-16.8,37.53-37.53,37.53Z"/>
            <path class="cls-1" d="m60.91,34.67c-.14-1.13-.85-3.26-.85-4.46s.71-3.33.85-4.46c.11-.82-.67-1.5-1.5-1.5h-5.8c-.67,0-1.21-.54-1.21-1.21h0c0-1.68-1.36-3.04-3.04-3.04h-3.85c-1.83,0-3.31,1.48-3.31,3.31v33.35c0,.9-.73,1.62-1.62,1.62h0c-1.92,0-3.48,1.56-3.48,3.48v11.75c0,1.92,1.56,3.48,3.48,3.48h13.46c1.92,0,3.48-1.56,3.48-3.48v-11.75c0-1.92-1.56-3.48-3.48-3.48h0c-.9,0-1.62-.73-1.62-1.62v-19.34c0-.64.52-1.16,1.16-1.16h5.85c.83,0,1.6-.68,1.5-1.5Z"/>
        </svg>
    {:else if cypher == "a1z26"}
        <svg style="--color: {fill_color}" class="icon {is_static ? "" : "icon_hover"}" id="a1z26" data-name="Layer 5" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 98 98">
            <path class="cls-1" d="m56.26,17.9l15.03-13.88c.79-.73,1.83-1.14,2.91-1.14h5.35c2.08,0,3.77,1.69,3.77,3.77v38.97c0,2.08-1.69,3.77-3.77,3.77h-3.52c-2.08,0-3.77-1.69-3.77-3.77v-26.55c0-1.08-1.31-1.62-2.07-.86l-6.92,6.92c-1.47,1.47-3.86,1.47-5.33,0l-1.8-1.8c-1.51-1.51-1.46-3.98.11-5.43Z"/>
            <path class="cls-1" d="m22.43,64H7.92c-1.61,0-2.92-1.65-2.92-3.68v-2.65c0-2.03,1.31-3.68,2.92-3.68h25.15c1.61,0,2.92,1.65,2.92,3.68v4.65c0,1.06-.36,2.07-1,2.77l-16.84,18.54c-.43.47-.16,1.36.41,1.36h14.5c1.61,0,2.92,1.65,2.92,3.68v2.65c0,2.03-1.31,3.68-2.92,3.68H7.92c-1.61,0-2.92-1.65-2.92-3.68v-4.54c0-1.13.39-2.21,1.07-2.96l16.77-18.46c.43-.47.16-1.36-.41-1.36Z"/>
            <path class="cls-1" d="m62.59,54h-15.18c-1.88,0-3.41,1.53-3.41,3.41v11.63c0,1.88,1.53,3.41,3.41,3.41h5.78c.33,0,.52.38.32.65l-8.83,11.77c-.44.59-.68,1.31-.68,2.05v4.68c0,1.88,1.53,3.41,3.41,3.41h15.18c1.88,0,3.41-1.53,3.41-3.41v-2.4c0-1.88-1.53-3.41-3.41-3.41h-5.78c-.33,0-.52-.38-.32-.65l8.83-11.77c.44-.59.68-1.31.68-2.05v-13.9c0-1.88-1.53-3.41-3.41-3.41Zm-4.57,11.27h-6.03c-.54,0-.98-.44-.98-.98v-2.13c0-.54.44-.98.98-.98h6.03c.54,0,.98.44.98.98v2.13c0,.54-.44.98-.98.98Z"/>
            <path class="cls-1" d="m76.99,95h16.01c1.65,0,2.99-1.34,2.99-2.99v-12.46c0-1.65-1.34-2.99-2.99-2.99h-8.83c-.56,0-.93-.57-.7-1.08l8.37-18.88c.54-1.22-.35-2.59-1.69-2.59h-4.22c-1.18,0-2.26.7-2.74,1.78l-8.75,19.74c-.3.68-.46,1.42-.46,2.16v14.33c0,1.65,1.34,2.99,2.99,2.99Zm4.99-11.27h6.03c.54,0,.98.44.98.98v2.13c0,.54-.44.98-.98.98h-6.03c-.54,0-.98-.44-.98-.98v-2.13c0-.54.44-.98.98-.98Z"/>
            <path class="cls-1" d="m56.27,44.67L40.73,5.77c-.7-1.74-2.38-2.89-4.26-2.89h-4c-1.85,0-3.51,1.11-4.23,2.81L11.88,44.53c-.89,2.12.66,4.47,2.97,4.47h4.01c1.3,0,2.46-.78,2.97-1.97l5.99-14.24c.2-.48.67-.79,1.19-.79h10.75c.53,0,1,.32,1.2.81l5.84,14.33c.5,1.23,1.71,2.03,3.04,2l3.49-.06c2.25-.04,3.77-2.32,2.93-4.41Zm-24.24-21.86l1.31-3.1c.43-1.02,1.89-1.02,2.31.01l1.26,3.1c.23.56-.18,1.18-.79,1.18h-3.29c-.61,0-1.02-.62-.79-1.19Z"/>
        </svg>
    {:else if cypher == "atbash"}
        Atbash
    {/if}

{:else}
    {#if cypher == "binary"}
        Binary
    {:else if cypher == ""}
        <span style="font-size: 35px;">⌂</span>
    {:else if cypher == "morse"}
        Morse
    {:else if cypher == "caesar"}
        Caesar
    {:else if cypher == "a1z26"}
        a1z26
    {:else if cypher == "atbash"}
        Atbash
    {:else if cypher == "qwer"}
        !"#¤
    {/if}
{/if}
