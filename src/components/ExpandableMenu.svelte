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
              <button type="button" on:click={() => item.expanded = !item.expanded}>
  <svg class="{item.expanded ? 'transform rotate-180' : ''} w-2 h-1 text-gray-100 transition-all duration-300" fill="none" stroke="currentColor" viewBox="0 0 12 6" xmlns="http://www.w3.org/2000/svg">
    <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="1" d="M19 9l-7 1-1-1"></path>
  </svg>
</button>

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
  .container {
    display: flex;
    min-height: 100vh;
    width: 100%;
  }

  .selected-document-container {
    flex: 1;
    padding: 2rem;
    background-color: #F3F4F6; /* Light Gray */
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .side-menu {
    width: 300px;
    max-width: 300px;
    background-color: #1E40AF; /* Blue */
    padding: 1rem;
    height: 100%;
    overflow-y: auto;
  }

  .menu-header {
    color: #FFF;
    font-size: 1.1rem;
    font-weight: 600;
    margin-bottom: 1rem;
  }

  .menu-item {
    margin-bottom: 1rem;
  }

  .menu-item a {
    color: #FFF;
    text-decoration: none;
    display: block;
    padding: 0.5rem;
  }

  .menu-item:hover {
    background-color: rgba(255, 255, 255, 0.1);
  }

  .menu-item.active {
    background-color: rgba(255, 255, 255, 0.2);
    border-radius: 0.25rem;
  }

  .submenu {
    margin-left: 1rem;
    margin-top: 0.5rem;
    padding-left: 0.5rem;
    border-left: 1px solid rgba(255, 255, 255, 0.2);
    display: none;
  }

  .submenu.active {
    display: block;
  }
  
  .sub-submenu {
    margin-left: 1rem;
    margin-top: 0.5rem;
    padding-left: 0.5rem;
    border-left: 1px solid rgba(255, 255, 255, 0.2);
    display: none;
  }

  .sub-submenu.active {
    display: block;
  }
</style>
