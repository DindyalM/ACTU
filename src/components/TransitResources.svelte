<script>
  let resources = [
  {
    id: 1,
    title: "Industry Report 2022",
    description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec ultrices, sem et pellentesque fermentum, sem augue aliquam nunc, in maximus lorem neque eu urna.",
    type: "file",
    file: "/reports/industry_report_2022.pdf"
  },
  {
    id: 2,
    title: "Best Practices Toolkit",
    description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec ultrices, sem et pellentesque fermentum, sem augue aliquam nunc, in maximus lorem neque eu urna.",
    type: "link",
    link: "https://www.example.com/best_practices_toolkit"
  },
  {
    id: 3,
    title: "Webinar Recordings",
    description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec ultrices, sem et pellentesque fermentum, sem augue aliquam nunc, in maximus lorem neque eu urna.",
    type: "video",
    file: "/webinars/webinar_recordings.mp4"
  }
];

let activeResource = null;

function setActiveResource(resource) {
  activeResource = resource;
}

function clearActiveResource() {
  activeResource = null;
}

</script>
<div class="menu-container">
  <ul class="menu-list">
    {#each resources as resource}
      <li class="menu-item">
        <button class="menu-link" on:click={() => setActiveResource(resource)}>{resource.title}</button>
      </li>
    {/each}
  </ul>
</div>

<div class="content-container">
  {#if activeResource}
    <div class="content-title">
      <h3>{activeResource.title}</h3>
    </div>
    <div class="content-description">
      <p>{activeResource.description}</p>
    </div>
    {#if activeResource.type === "file"}
      <div class="content-file">
        <a href={activeResource.file} target="_blank">Download File</a>
      </div>
    {:else if activeResource.type === "video"}
      <div class="content-video">
        <video controls>
          <source src={activeResource.file} type="video/mp4">
          Your browser does not support the video tag.
        </video>
      </div>
    {:else if activeResource.type === "link"}
      <div class="content-link">
        <a href={activeResource.link} target="_blank">Visit Link</a>
      </div>
    {/if}
    <button class="close-button" on:click={clearActiveResource}>Close</button>
  {/if}
</div>

