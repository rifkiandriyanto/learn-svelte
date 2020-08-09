<script>
  import EmojiDisplay from './components/EmojiDisplay.svelte';
  import EmojiDescription from './components/EmojiDescription.svelte';
  import Button from './components/Button.svelte';
  import { fade, fly } from 'svelte/transition'

  let isLoaded = false;
  let currentEmoji = '😀';
  const emojis = ['😅', '🦊', '🐵', '🐊', '🚀'];
  let mouse = { x: 0, y: 0 };

  function randomizeEmoji() {
    return emojis[Math.floor(Math.random() * emojis.length)];
  }

  function handleRandomButton() {
    currentEmoji = randomizeEmoji();
  }

  function handleMouseMove(event) {
    mouse.x = event.clientX;
    mouse.y = event.clientY;
  }

  setTimeout(() => {
    isLoaded = true;
  }, 3000);
</script>

<svelte:head>
  <link href="/terminal.min.css" rel="stylesheet" />
</svelte:head>

<div class="container" on:mousemove={handleMouseMove}>
  <p>The mouse position: {mouse.x} x {mouse.y}</p>
  <h1>Randomize Emoji</h1>
  {#each emojis as emoji}
    <ul>
      <li>{emoji}</li>
    </ul>
  {/each}

  {#if isLoaded === true}
    <div in:fly={{y: 200, duration: 2000}} out:fade>
      <br />
      <EmojiDisplay {currentEmoji} />
      <EmojiDescription />
    </div>
  {:else}
    <h2>Loading ....</h2>
  {/if}

  <Button on:click={handleRandomButton} title={'🦄 Randomize'} />
  <Button title="toggle" on:click={() => (isLoaded = !isLoaded)} />
</div>
