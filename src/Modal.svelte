<!-- svelte components have 3 parts, script for code, 
    HTML for rendering data, stle for declaring style -->
<script>
    export let showModal = false;
    // When receiving props inside of a component you use the export keyword
    // you can set defaults as well
    export let isPromo = false;


 
</script>
    <!-- {#if} to start an if statement in svelte, close if block with {/if}
    {:else} and {:else if} to add conditional logic in svelte-->
{#if showModal}
<!-- can add conditional classes to css and make this change in the css-->
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div class ="backdrop" class:promo = {isPromo} on:click|self>
        <div class = "modal">
            
            <slot></slot>
        </div>
    </div>
    
{/if}
<style>
    .backdrop{
        width:100%;
        height:100%;
        position:fixed;
        background:rgba(0,0,0,0.8)
    }
    .modal{
        padding:10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 10% auto;
        text-align: center;
        background: white;
    }
    /* <!-- can add conditional classes to css and make this change in the css--> */
    .promo .modal{
      background: crimson;
      color: white;
    }
</style>