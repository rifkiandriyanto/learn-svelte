<script>
  import { onMount, onDestroy, beforeUpdate, afterUpdate } from 'svelte';
  let description = '';

  $: characters = description.length;
  $: words = description.split(' ').length;
  $: if (description.length > 10) {
    console.log('-------------');
    console.log(`Desription: ${description}`);
  }

  function handleSubmit() {
    event.preventDefault();
    console.log('Haaaaaaahaaaaaaaaaaa');
    description = '';
  }

  onMount(function () {
    console.log('ini ======> onMount');
  });

  onDestroy(function () {
    console.log('ini ======> onDestroy');
  });

  afterUpdate(function () {
    console.log('ini ======> afteUpdate');
  });

  beforeUpdate(function () {
    console.log('ini ======> beforeUpdate');
  });
</script>

<style>
  div {
    margin-top: 1em;
    margin-bottom: 1em;
  }
</style>

<div class="form-group">
  <form on:submit={handleSubmit}>
    <textarea bind:value={description} rows="7" />
    <button class="btn btn-primary" type="submit">Save</button>
  </form>

  <p>Charaters count: {characters}</p>
  <p>Words count: {words}</p>
</div>
