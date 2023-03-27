<script>
  import { createEventDispatcher } from "svelte";

  export let title = "";
  export let items = [];
  let expanded = false;

  const dispatch = createEventDispatcher();

  function toggle() {
    expanded = !expanded;
  }

  function selectDocument(item) {
    if (item.items) {
      item.expanded = !item.expanded;
    } else {
      dispatch("select", item);
    }
  }
</script>
<div class="w-full">
  <button
    on:click="{toggle}"
    class="menu-title text-lg font-semibold focus:outline-none"
  >
    {title}
    <svg
      class="{expanded ? 'transform rotate-180' : ''} w-4 h-4 text-white transition-all duration-300"
      fill="none"
      stroke="currentColor"
      viewBox="0 0 24 24"
      xmlns="http://www.w3.org/2000/svg"
      width="16"
      height="16" 
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
    <ul class="list-disc ml-4 nested-menu {expanded ? 'expanded' : ''}">
      <!-- ... -->
      {#each items as item}
        <li class="mb-1">
          <div class="flex items-center justify-between">
            <button
              on:click={() => selectDocument(item)}
              class="text-left focus:outline-none focus:ring-2 focus:ring-indigo-400"
            >
              {item.title}
            </button>
            {#if item.items}
              <svg
                class="{item.expanded ? 'transform rotate-180' : ''} w-1 h-1 text-gray-100 transition-all duration-300"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 12 6"
                xmlns="http://www.w3.org/2000/svg"
                on:click={() => item.expanded = !item.expanded}
              >
                <path
                  strokeLinecap="round"
                  strokeLinejoin="round"
                  strokeWidth="1"
                  d="M19 9l-7 1-1-1"
                ></path>
              </svg>
            {/if}
          </div>
          {#if item.expanded}
            <ul class="list-disc ml-4">
              {#each item.items as subitem}
                <li class="mb-1">
                  <button
                    on:click={() => selectDocument(subitem)}
                    class="text-left focus:outline-none focus:ring-2 focus:ring-indigo-400"
                  >
                    {subitem.title}
                  </button>
                </li>
              {/each}
            </ul>
          {/if}
        </li>
      {/each}
    </ul>
  {/if}
</div>
<style>
 
</style>
