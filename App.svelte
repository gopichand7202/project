<script>
  import {ContentSwitcher,Switch} from 'carbon-components-svelte';
  import Online from './lib/online.svelte';
  import Offline from './lib/offline.svelte';


  let currentpage="online";
  function handleSwitch(page){
    currentpage=page;
  }

</script>

<style>
  .switch {
    position: absolute;
    top: 0; /* Aligns to the top */
    left: 0; /* Aligns to the left */
    padding: 10px; /* Optional: Adds some padding */
  }
  .switch{
    width: 175px; /* Set desired width here */
  }
</style>

<div class="switch">
<ContentSwitcher  size='sm'>
  <Switch text="online" on:click= {()=> handleSwitch('online')}/>
  <Switch text="offline" on:click={()=>handleSwitch('offline')}/>
</ContentSwitcher>
</div>

<div class="pages">
  {#if currentpage === 'online'}
    <Online />  <!-- Render Online component -->
  {:else}
    <Offline /> <!-- Render Offline component -->
  {/if}
</div>