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
  import { nanoid } from "nanoid";

  import { Router, onUpgrade } from "vibemenu";

  const todos = getTodos();
  const settings = getSettings();

  function setInitialValue() {
    const firstTodo = {
      id: nanoid(),
      completed: false,
      description: "First todo!",
    };

    todos.push(firstTodo);
    $settings.placeholderText = "Press Enter to create todo!";
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

  /*Install default font used in vibemenu*/
  /*
  @font-face {
    font-family: "Varela Round script=latin rev=1";
    font-style: normal;
    font-weight: 400;
    font-display: block;
    src: url(https://vibe.menu/_app/assets/VarelaRound-Regular-d82847cb.ttf)
      format("woff2");
  }*/
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
