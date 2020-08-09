<script>
  export let currentEmoji;
  let current = 'button1';
</script>

<style>
  div {
    font-size: 3em;
    margin-bottom: 0.5em;
  }
  button {
    color: orange;
    border-radius: 5px;
  }
  .active {
    background-color: #ff3e00;
    color: #fff;
  }
</style>

<div>{currentEmoji}</div>
<h1>JS function</h1>
<button
  class={current === 'button1' ? 'active' : ''}
  on:click={() => (current = 'button1')}>
  Button 1
</button>
<button
  class={current === 'button2' ? 'active' : ''}
  on:click={() => (current = 'button2')}>
  Button 2
</button>
<button
  class={current === 'button3' ? 'active' : ''}
  on:click={() => (current = 'button3')}>
  Button 3
</button>
<br />

<h1>Svelte.js function</h1>
<button
  class:active={current === 'button1'}
  on:click={() => (current = 'button1')}>
  Button 1
</button>
<button
  class:active={current === 'button2'}
  on:click={() => (current = 'button2')}>
  Button 2
</button>
<button
  class:active={current === 'button3'}
  on:click={() => (current = 'button3')}>
  Button 3
</button>
