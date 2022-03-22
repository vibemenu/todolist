<script context="module" lang="ts">
  import { state } from "vibemenu";

  export type Todo = { id: string; completed: boolean; description: string };
  type State = {
    todos: Array<Todo>;
    settings: { placeholderText: string };
  };

  export const getState = () => state<State>();
  export const getTodos = () => getState().getArray("todos");
  export const getSettings = () => getState().get("settings");
</script>

<script>
  import { Router, onUpgrade } from "vibemenu";

  const state2 = getState();

  function setInitialValue() {
    $state2 = {
      todos: [],
      settings: {
        placeholderText: "Press Enter to create todo!",
      },
    };
  }

  onUpgrade((version) => {
    if (version === undefined) {
      setInitialValue();
      version = 0;
    }

    return version;
  });
</script>

<Router
  routes={{
    "/": () => import("./Todos.svelte"),
    "/settings": () => import("./Settings.svelte"),
  }}
/>

<svelte:head>
  <!-- Install default font used in vibemenu -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link
    href="https://fonts.googleapis.com/css2?family=Varela+Round&display=swap"
    rel="stylesheet"
  />
</svelte:head>

<style global lang="postcss">
  /*Install tailwindcss*/
  @tailwind base;
  @tailwind components;
  @tailwind utilities;

  /*Hide scrollbar in body*/
  body {
    @apply scrollbar-hide;
    overflow: hidden;
    font-family: "Varela Round";
  }
  /*Make background transparent*/
  html {
    @apply bg-opacity-0;
  }
</style>
