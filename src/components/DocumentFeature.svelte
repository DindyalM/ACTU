<script>
  import ExpandableMenu from "./ExpandableMenu.svelte";

  let search = "";
  let exampleData = [
    {
      title: "General Document",
      items: [
        { title: "AGM", content: "This is an example AGM document." },
        { title: "Annual Reports", content: "This is an example annual report document." },
        { title: "By-Laws", content: "This is an example by-laws document." },
      ],
    },
    {
      title: "Committees",
      items: [
        {
          title: "Administrative",
          items: [
            { title: "Board of Committee", content: "This is an example Board of Committee document." },
            { title: "Governance Committee", content: "This is an example Governance Committee document." },
            { title: "Audit Committee", content: "This is an example Audit Committee document." },
            { title: "Nominating Committee", content: "This is an example Nominating Committee document." },
            { title: "Regional Chairs Committee", content: "This is an example Regional Chairs Committee document." },
            { title: "Executive Committee", content: "This is an example Executive Committee document." },
          ],
        },
        {
          title: "Regional Committees",
          items: [
            {
              title: "BC Regional Committee",
              items: [{ title: "Safety & Security Committee", content: "This is an example Safety & Security Committee document." }],
            },
            { title: "Prairie Provinces Committee", content: "This is an example Prairie Provinces Committee document." },
            { title: "Ontario Regional Committee", content: "This is an example Ontario Regional Committee document." },
            { title: "Quebec Regional Committee", content: "This is an example Quebec Regional Committee document." },
            { title: "Atlantic Regional Committee", content: "This is an example Atlantic Regional Committee document." },
          ],
        },
      ],
    },
  ];

  let selectedDocument = null;
  let filteredData = exampleData;

  function handleSelectDocument(event) {
  selectedDocument = event.detail;
  console.log(selectedDocument);
}


  function updateSearch(event) {
    search = event.target.value;
    if (search.trim() === "") {
      filteredData = exampleData;
    } else {
      filteredData = exampleData.map((data) => {
        const filteredItems = data.items.filter((item) =>
          item.title.toLowerCase().includes(search.toLowerCase())
        );
        return {
          ...data,
          items: filteredItems,
        };
      });
    }
  }
</script>


<div class="flex w-full min-h-screen">
  <div class="w-1/2 p-8">
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

  <div class="w-1/2 p-8">
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
          />
        {/if}
      {/each}
    </div>
  </div>
</div>


