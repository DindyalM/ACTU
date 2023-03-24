<script>
  import ExpandableMenu from "./ExpandableMenu.svelte";
  let search = "";
  let exampleData = [
    {
      title: "General Document",
      items: ["AGM", "Annual Reports", "By-Laws"]
    },
    {
      title: "Committees",
      items: [
        "Administrative",
        "Regional Committees",
        "National",
      ]
    },
    // Add more sections if needed
  ];
</script>

<div class="flex w-full min-h-screen">
  <div class="w-1/2 p-8">
    <h2 class="text-3xl mb-4">Selected Document</h2>
    <div class="overflow-y-auto h-full">
      <!-- Add your documents here with appropriate classes and styles -->
    </div>
  </div>

  <div class="w-1/2 p-8">
    <div class="mb-4">
      <input
        type="text"
        placeholder="Search documents"
        bind:value="{search}"
        class="w-full px-3 py-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-indigo-400"
      />
    </div>

    <div class="overflow-y-auto h-full">
      {#each exampleData as data}
        <ExpandableMenu title="{data.title}" items="{data.items}" />
      {/each}
    </div>
  </div>
</div>

<style>
  .overflow-y-auto {
    scrollbar-width: thin;
  }
  .overflow-y-auto::-webkit-scrollbar {
    width: 6px;
  }
  .overflow-y-auto::-webkit-scrollbar-thumb {
    background-color: rgba(107, 114, 128, 0.5);
    border-radius: 9999px;
  }
</style>
