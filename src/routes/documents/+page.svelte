<script>
  import DocumentFeature from "../../components/DocumentFeature.svelte";
  import TransitResources from "../../components/TransitResources.svelte"
</script>

<main class="h-screen bg-gray-100">
  <div class="flex flex-col items-center justify-center">
    <h3 class="text-3xl font-semibold mb-2">Transit Resources</h3>
    <TransitResources />
  </div>
  
  <div class="flex flex-col items-center justify-center h-full">
    <h3 class="text-3xl font-semibold mb-2">HR Feature</h3>
    <DocumentFeature />
  </div>
</main>

<style>
  .h-screen {
    height: 100vh;
  }

  .bg-gray-100 {
    background-color: #f3f4f6;
  }

  .flex {
    display: flex;
  }

  .flex-col {
    flex-direction: column;
  }

  .items-center {
    align-items: center;
  }

  .justify-center {
    justify-content: center;
  }

  .h-full {
    height: 100%;
  }
</style>
