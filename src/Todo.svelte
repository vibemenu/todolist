<script lang="ts">
  import type { State } from "vibemenu";
  export let todo: State<{completed: boolean;id: string; description: string;}>;
</script>
<div class="flex rounded my-2 p-2 {$todo.completed? 'bg-green-200': 'bg-gray-100'} items-center">
  <input class="m-2" type="checkbox" bind:checked={$todo.completed} />
  <div class="flex-grow" contenteditable bind:textContent={$todo.description} />
  <button class="m-1" on:click={todo.deleteThis}>x</button>
</div>