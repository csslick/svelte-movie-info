<script>
  import { fly } from 'svelte/transition';

  let isEvent = true; // 이벤트 팝업 여부
  export let eventText = [];
  export let eventIndex = 0;
</script>

<!-- <div class={isEvent? 'event show' : 'event'}> -->
{#if isEvent}  
  <div class="event" transition:fly={{ y: -400, duration: 1000 }}>
    <p>{eventText[eventIndex]}</p>
    <button on:click={()=> isEvent=false}>X</button>
  </div>
{/if}

<style>
  .event {
    width: 100%;
    background: #666;
    padding: 5px 1em;
    font-size: small;
    text-align: center;
    color: #fff;
    text-align: center;
    margin-bottom: 1em;
    position: relative;
  
    /* 창이 보이지 않게 */
    /* max-height: 0;
    opacity: 0; 
    overflow: hidden;
    transition: all 0.4s; */
  }
  
  /* 기본: 창이 보이게 */
  .show {
    opacity: 1;
    max-height: 100px;
  }
  
  .event button {
    padding: 2px;
    position: absolute;
    right: 20px;
    top: 15px;
  }

</style>