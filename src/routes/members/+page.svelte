<script>
  import { onMount } from 'svelte';
  import members from '../../members.json';
  
  let companies = [];
  let filteredCompanies = [];
  let filteredMembers = [];
  let selectedCompany = '';
  let searchTerm = '';
  let memberSearchTerm = '';

  function handleCompanyClick(companyName) {
    selectedCompany = companyName;
    filteredMembers = members.filter(member => member.company === selectedCompany && (member.name.toLowerCase().includes(memberSearchTerm.toLowerCase()) || member.email.toLowerCase().includes(memberSearchTerm.toLowerCase())));
  }

  function handleCompanySearch(event) {
    const { value } = event.target;
    searchTerm = value;
    filteredCompanies = companies.filter(company => company.toLowerCase().includes(value.toLowerCase()));
  }

  function handleMemberSearch(event) {
    const { value } = event.target;
    memberSearchTerm = value;
    filteredMembers = members.filter(member => member.company.toLowerCase().includes(searchTerm.toLowerCase()) && (member.name.toLowerCase().includes(value.toLowerCase()) || member.email.toLowerCase().includes(value.toLowerCase())));
    if (filteredMembers.length > 0) {
      selectedCompany = filteredMembers[0].company;
    } else {
      selectedCompany = '';
    }
    filteredCompanies = companies.filter(company => company.toLowerCase().includes(searchTerm.toLowerCase()) && members.some(member => member.company === company && (member.name.toLowerCase().includes(value.toLowerCase()) || member.email.toLowerCase().includes(value.toLowerCase()))));
  }

  function clearSearch() {
    searchTerm = '';
    memberSearchTerm = '';
    filteredCompanies = companies;
    filteredMembers = [];
    selectedCompany = '';
  }

  onMount(() => {
    // Populate list of companies
    companies = Array.from(new Set(members.map(member => member.company)));
    filteredCompanies = companies;
  });
</script>
<div class="flex flex-col items-center">
  <h1 class="text-3xl font-bold my-4">Member Search</h1>

  <!-- Company selection -->
  <div class="w-full md:w-1/2">
    <form>
      <label class="block my-4">
        <span class="text-gray-700">Search Companies:</span>
        <input type="text" class="form-input mt-1 block w-full" on:input={handleCompanySearch}>
      </label>
    </form>

    <ul class="flex flex-col space-y-2 my-4">
      {#each filteredCompanies as company}
        <li>
          <button class="px-2 py-1 rounded bg-gray-200 hover:bg-gray-300 focus:outline-none" on:click={() => handleCompanyClick(company)}>{company}</button>
        </li>
      {/each}
    </ul>
  </div>

  <!-- Members search -->
  <div class="w-full md:w-1/2">
    <form>
      <label class="block my-4">
        <span class="text-gray-700">Search Members:</span>
        <input type="text" class="form-input mt-1 block w-full" on:input={handleMemberSearch}>
      </label>
    </form>

    {#if filteredMembers.length === 0}
      <p class="text-gray-700 my-4">No members found.</p>
    {:else}
      <ul class="my-4">
        {#each filteredMembers as member (member.id)}
          <li class="my-2">
            <strong>{member.name}</strong>
            <br>
            {member.email} - {member.company}
          </li>
        {/each}
      </ul>
    {/if}
  </div>
</div>

