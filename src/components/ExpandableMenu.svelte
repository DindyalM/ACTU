<script>
  export let title = "";
  export let items = [];
  let expanded = false;

  function toggle() {
    expanded = !expanded;
  }

  function selectDocument(item) {
    dispatch("select", item);
  }
</script>


<div class="w-full">
  <button
    on:click="{toggle}"
    class="w-full flex items-center justify-between py-2 text-left text-lg font-semibold focus:outline-none focus:ring-2 focus:ring-indigo-400"
  >
    {title}
    <svg
      class="{expanded ? 'transform rotate-180' : ''} w-4 h-4 text-gray-500 transition-all duration-300"
      fill="none"
      stroke="currentColor"
      viewBox="0 0 24 24"
      xmlns="http://www.w3.org/2000/svg"
    >
      <path
        strokeLinecap="round"
        strokeLinejoin="round"
        strokeWidth="2"
        d="M19 9l-7 7-7-7"
      ></path>
    </svg>
  </button>
  {#if expanded}
    <ul class="list-disc ml-4">
      {#each items as item}
        {#if item.items}
          <li class="mb-1">
            <ExpandableMenu
              title={item.title}
              items={item.items}
              on:select={selectDocument}
            />
          </li>
        {:else}
          <li class="mb-1">
            <button on:click={() => selectDocument(item)} class="text-left focus:outline-none focus:ring-2 focus:ring-indigo-400">
              {item.title}
            </button>
          </li>
        {/if}
      {/each}
    </ul>
  {/if}
</div>

