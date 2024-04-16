<script>
  import { fly, fade } from 'svelte/transition';

  export let isEvent;
  export let eventText;
  export let eventIndex;
</script>

<div 
  class='event show' 
  in:fly={{ y: -400, duration: 1000}}
  out:fade
>
  <p>{eventText[eventIndex]}</p>
  <button on:click={() => isEvent=false}>X</button>
</div>

<style>
  .event {
    width: 100%;
    background: #666;
    padding: 5px 1em;
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: #fff;
    text-align: center;
    margin-bottom: 1em;
    padding: 10px 20px;

    /* 창이 보이지 않게 */
    max-height: 0;
    opacity: 0;
    overflow: hidden;
    transition: all 0.4s;
  }

  /* 기본: 창이 보이게 */
  .show {
    opacity: 1;
    max-height: 100px;
  }

  .event button {
    padding: 2px;
  }

  .event p, .event button {
    margin: 0;
  }
  .event p {
    width: 100%;
  }
</style>
