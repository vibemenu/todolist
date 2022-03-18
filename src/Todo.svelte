<script lang="ts">
  import type { State } from "vibemenu";
  import type { Todo } from "./App.svelte";
  export let todo: State<Todo>;
</script>

<div
  class="flex rounded my-2 p-2 {$todo.completed
    ? 'bg-green-200'
    : 'bg-gray-100'} items-center"
>
  <input class="m-2" type="checkbox" bind:checked={$todo.completed} />
  <div class="flex-grow" contenteditable bind:textContent={$todo.description} />
  <button class="m-1" on:click={todo.deleteThis}>x</button>
</div>
