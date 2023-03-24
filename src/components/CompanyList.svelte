<script>
  import { onMount } from 'svelte';
  import { writable } from 'svelte/store';
  import companies from '../companies.json';

  export const selectedCompany = writable(null);

  let filteredCompanies = [];
  let searchTerm = '';

  function handleSubmit(event) {
    event.preventDefault();
    filteredCompanies = companies.filter(company => {
      return company.toLowerCase().startsWith(searchTerm.toLowerCase());
    });
  }

  onMount(() => {
    filteredCompanies = companies;
  });
</script>

<div>
  <form on:submit={handleSubmit}>
    <label>
      Search:
      <input type="text" bind:value={searchTerm}>
    </label>
    <button type="submit">Search</button>
  </form>

  <div>
    {#each filteredCompanies as company}
      <button on:click={() => selectedCompany.set(company)}>{company}</button>
    {/each}
  </div>
</div>
