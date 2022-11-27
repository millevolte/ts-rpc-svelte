<script lang="ts">
  import { server } from "../GeneratedCode/generatedTypescript";
  let count: number = 0;
  let result: string = "";
  let result2 = "";
  let result3 = {};

  const testGet = async () => {
    const { data, error } = await server.Ping();
    if (!error) {
      result = data;
    }
  };

  const testGetParams = async () => {
    const { data, error } = await server.PingParams("100", "200");
    if (!error) {
      result2 = data;
    }
  };

  const testPost = async () => {
    const input = <server.FormRequest>{ req: "pippo", count: count };
    const { data, error } = await server.Post(input);
    if (!error) {
      result3 = data;
    }
    count++;
  };
</script>

<div class="flex m-2 mb-4 p-2 border-2 border-rose-600 ">
  <div class="flex w-1/6 h-12 items-start">
    <button
      on:click={testGet}
      class="px-5 py-3 text-white bg-red-500 border-solid shadow-md whitespace-nowrap hover:bg-red-600 focus:ring-1 focus:outline-none focus:ring-opacity-30"
    >
      Test GET
    </button>
  </div>
  <div class="flex w-5/6 h-12 ml-8 items-start">
    {result}
  </div>
</div>

<div class="flex m-2 mb-4 p-2 border-2 border-rose-600 ">
  <div class="flex w-2/6 h-12 items-start">
    <button
      on:click={testGetParams}
      class="px-5 py-3 text-white bg-red-500 border-solid shadow-md whitespace-nowrap hover:bg-red-600 focus:ring-1 focus:outline-none focus:ring-opacity-30"
    >
      Test GET whit params
    </button>
  </div>
  <div class="flex w-5/6 h-12 items-start  ml-8 ">
    {result2}
  </div>
</div>

<div class="m-2 mb-4 p-2 border-2 border-rose-600 grid grid-cols-6 ">
  <div class="col-2 text-left" style="min-width: 120px; width: 120px;">
    <div class="w-100 ">
      <input
        bind:value={count}
        type="number"
        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
        required
      />
    </div>
    <br />
    <div class="mt-2">
      <button
        on:click={testPost}
        class="px-5 py-3 text-white bg-red-500 border-solid shadow-md whitespace-nowrap hover:bg-red-600 focus:ring-1 focus:outline-none focus:ring-opacity-30"
      >
        Test Post
      </button>
    </div>
  </div>
  <div class="col-span-4 text-left ml-8">
    {JSON.stringify(result3)}
  </div>
</div>
