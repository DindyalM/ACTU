<script>
  import ExpandableMenu from "./ExpandableMenu.svelte";

  let search = "";
  let exampleData = [    {      title: "General Document",      items: [        { title: "AGM" },        { title: "Annual Reports" },        { title: "By-Laws" },      ],
    },
    {
      title: "Committees",
      items: [
        {
          title: "Administrative",
          items: [
            { title: "Board of Committee" },
            { title: "Governance Committee" },
            { title: "Audit Committee" },
            { title: "Nominating Committee" },
            { title: "Regional Chairs Committee" },
            { title: "Executive Committee" },
          ],
        },
        {
          title: "Regional Committees",
          items: [
            {
              title: "BC Regional Committee",
              items: [{ title: "Safety & Security Committee" }],
            },
            { title: "Prairie Provinces Committee" },
            { title: "Ontario Regional Committee" },
            { title: "Quebec Regional Committee" },
            { title: "Atlantic Regional Committee" },
          ],
        },
        {
          title: "National",
          items: [
            { title: "Business Members National Committee" },
            { title: "Business Members North American Pavilion/Day Taskforce" },
            { title: "Communication & Public Affairs National Committee" },
            {
              title: "Workforce Development National Committee",
              items: [
                { title: "Awards and Recognition Sub-Committee" },
                { title: "Youth and Emerging Leaders Sub-Committee" },
                { title: "Labour Relations Networking Group" },
                { title: "Talent Acquisition & Recruiters Networking Group" },
                { title: "Driver Trainers Networking Group" },
              ],
            },
            {
              title: "Technical Service National Committee",
              items: [
                { title: "Maintenance & Vehicle Technology Sub-Committee" },
                { title: "Planning & ITS Sub-Committee" },
                { title: "Statistics Sub-Committee" },
                { title: "Accessible Transit Sub-Committee" },
                { title: "Mobility Management Implementation Taskforce" },
                { title: "Transit Board Members National Committee" },
              ],
            },
          ],
        },
      ],
    },
  ];


  let selectedDocument = null;
  let filteredData = exampleData;

  function handleSelectDocument(event) {
    selectedDocument = event.detail;
  }

 function updateSearch(event) {
  showMenu = false; // add this line to always close all menus
  showMembers = false;
  search = event.target.value.toLowerCase();
  filteredOptions = options.filter(option =>
    option.label.toLowerCase().includes(search)
  );



  if (search.trim() === "") {
    // If the search query is empty, show all items
    filteredData = exampleData;
  } else {
    // If the search query is not empty, filter the items and sub-items based on the query
    filteredData = exampleData.map(data => {
      const filteredItem = { ...data };
      filteredItem.items = filteredItem.items.filter(item => {
        if (item.title.toLowerCase().includes(search)) {
          return true;
        } else if (item.items) {
          const filteredSubItems = item.items.filter(subItem => subItem.title.toLowerCase().includes(search));
          if (filteredSubItems.length > 0) {
            item.items = filteredSubItems;
            return true;
          }
        }
        return false;
      });

      return filteredItem;
    }).filter(data => data.items.length > 0);
  }
}


</script>

<div class="container">
  <div class="selected-document-container">
    <h2 class="text-3xl mb-4">Selected Document</h2>
    <div class="overflow-y-auto h-full">
      {#if selectedDocument}
        <div class="p-4 bg-white shadow rounded">
          <h3 class="text-2xl font-semibold mb-2">{selectedDocument.title}</h3>
          <p>{selectedDocument.content}</p>
        </div>
      {:else}
        <p>No document selected</p>
      {/if}
    </div>
  </div>

 <div class="side-menu">
    <input
      type="text"
      placeholder="Search documents..."
      bind:value="{search}"
      on:input="{updateSearch}"
      class="w-full p-2 mb-4 bg-white border border-gray-300 rounded shadow focus:outline-none focus:ring-2 focus:ring-indigo-400"
    />

    <div class="overflow-y-auto h-full">
      {#each filteredData as data}
        {#if data.items.length > 0}
          <ExpandableMenu
            title="{data.title}"
            items="{data.items}"
            on:select="{handleSelectDocument}"
            selectedDocument="{selectedDocument}"
          />
        {/if}
      {/each}
    </div>
  </div>
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

.menu-title {
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: #FFF;
  font-size: 1.1rem;
  font-weight: 600;
  margin-bottom: 1rem;
  background-color: #1E40AF; /* Blue */
  padding: 0.5rem;
  border-radius: 0.25rem;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.menu-title:hover {
  background-color: rgba(255, 255, 255, 0.2);
}

.menu-title:focus {
  outline: none;
}

.menu-title svg {
  fill: none;
  stroke: #FFF;
  transition: transform 0.3s ease;
}

.menu-title:focus svg,
.menu-title:hover svg {
  stroke: rgba(255, 255, 255, 0.8);
}

.nested-menu {
  margin-top: 0.5rem;
  padding-left: 1rem;
  display: none;
}

.expanded .nested-menu {
  display: block;
}

.menu-item {
  margin-bottom: 0.5rem;
}

.menu-item button {
  color: #FFF;
  text-decoration: none;
  display: block;
  padding: 0.5rem;
  background-color: transparent;
  border: none;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.menu-item button:focus,
.menu-item button:hover {
  background-color: rgba(255, 255, 255, 0.2);
}

.menu-item.active button {
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
