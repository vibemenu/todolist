<script>
  import { Router } from "vibemenu";
</script>

<Router
  routes={{
    "/": () => import("./Todos.svelte"),
    "/settings": () => import("./Settings.svelte")
  }}
/>


<svelte:head>
  <!-- Install default font used in vibemenu -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Varela+Round&display=swap" rel="stylesheet">
</svelte:head>

<style global>
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
  html{
    @apply bg-opacity-0;
  }
</style>
