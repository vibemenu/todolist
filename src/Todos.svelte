<script lang="ts">
  import Todo from "./Todo.svelte";
  import { nanoid as uuid } from "nanoid";
  import { getTodos, getSettings } from "./App.svelte";
  const settings = getSettings();
  const todos = getTodos();
  const add = (input) => {
    todos.insert(0, { id: uuid(), completed: false, description: input.value });
    input.value = "";
  };
</script>

<input
  on:keydown={(event) => event.key === "Enter" && add(event.target)}
  class="p-2 outline-gray-300 border-2 border-gray-200 text-base text-center my-8 w-full"
  placeholder={$settings.placeholderText}
/>
{#each $todos as todo (todo.id)}
  <Todo todo={todos.getById(todo.id)} />
{/each}
