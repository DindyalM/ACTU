<script>
  let activeReport = null;

  const reports = [
    { title: 'New Members Report', description: 'Lists all members that have joined CUTA from the current year and from November of the past year' },
    { title: 'Non-Renewed Members', description: 'Lists organizations + primary contact name and email + membership fees for tracking purposes' },
    { title: 'Renewed Members', description: 'Lists organizations + membership fees for tracking purposes' },
    { title: 'Resigned and Terminated Members Report', description: 'Lists date of termination + reason from organizations\' notes section' },
    { title: 'Primary Contacts Report', description: 'Lists all primary contacts names, titles, and contact information' },
    { title: 'Active Contacts Report', description: 'Lists all CUTA active contacts, their organization, title, and contact information' },
    { title: 'Members by Title Report', description: 'With a search option' },
    { title: 'Expressions Newsletter Subscribers Report', description: '' },
    { title: 'Committee Members Report', description: 'For each committee - Lists all members\' emails, organization, and job title' },
    { title: 'Board Members Report', description: 'Lists all board members, organizations, contact information, and titles' },
    { title: 'Executive Committee Report', description: 'Lists all executive members, organizations, contact information, and titles' }
  ];

  function setActiveReport(report) {
    activeReport = report;
  }

  function clearActiveReport() {
    activeReport = null;
  }
</script>

<div class="reports-container">
  <h3>Reports</h3>
  <div class="report-list">
    {#each reports as report}
      <div class="report" on:click={() => setActiveReport(report)}>
        <h4>{report.title}</h4>
        <p>{report.description}</p>
      </div>
    {/each}
  </div>
  {#if activeReport !== null}
    <div class="report-details">
      <h4>{activeReport.title}</h4>
      <p>{activeReport.description}</p>
      <button on:click={clearActiveReport}>Close</button>
    </div>
  {/if}
</div>
<style>
  .report-container {
    max-width: 800px;
    margin: 0 auto;
    text-align: center;
  }

  .report-container h3 {
    font-size: 2rem;
    margin-bottom: 1rem;
  }

  .buttons {
    display: flex;
    justify-content: center;
    margin-bottom: 1rem;
  }

  button {
    background-color: #FFF;
    color: #000;
    border: 1px solid #000;
    border-radius: 5px;
    padding: 0.5rem;
    margin-right: 1rem;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  button.active {
    background-color: #000;
    color: #FFF;
  }

  .report-content {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .report {
    margin-top: 2rem;
    width: 100%;
    overflow-x: auto;
  }

  .report table {
    border-collapse: collapse;
    width: 100%;
  }

  .report th, .report td {
    border: 1px solid #ddd;
    padding: 0.5rem;
    text-align: center;
  }

  .report th {
    background-color: #f2f2f2;
    font-weight: bold;
  }

  .report td {
    vertical-align: middle;
  }

  .search {
    margin-top: 2rem;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .search label {
    margin-right: 0.5rem;
    font-weight: bold;
  }

  .search input {
    padding: 0.5rem;
    border-radius: 5px;
    border: 1px solid #ccc;
    width: 100%;
    max-width: 400px;
  }

  @media (min-width: 768px) {
    .report-content {
      flex-direction: row;
    }

    .report {
      margin-top: 0;
      margin-left: 2rem;
      margin-right: 2rem;
      width: auto;
      overflow-x: visible;
    }

    .search {
      margin-top: 0;
      margin-left: 2rem;
      margin-right: 2rem;
    }

    .search input {
      width: auto;
      max-width: 100%;
    }
  }
</style>


