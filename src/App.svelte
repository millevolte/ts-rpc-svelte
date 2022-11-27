<script lang="ts">
  import logo from "./assets/svelte.svg";
  import TsRpcTest from "./lib/TsRpcTest.svelte";
</script>

<main class="text-center">
  <img class="mx-auto" src={logo} alt="Svelte Logo" />
  <h1 class="p-3 text-lg font-bold">Typescript Ghost Bridege</h1>

  <TsRpcTest />

  <p class="p-2 mt-10 text-sm">
    Visit <a href="https://github.com/millevolte/ts-rpc">Ghost Bridge source code</a>
    to learn how to use TsRpc in your app.
  </p>
</main>

<style>
  a {
    @apply text-blue-700;
  }
  a:hover {
    @apply underline;
  }
</style>
