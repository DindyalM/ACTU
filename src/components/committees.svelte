<div class="committee-container">
  <div class="board-members">
    <h3>Board Members</h3>
    <ul>
      {#each boardMembers as member}
        <li>{member.name}</li>
      {/each}
    </ul>
  </div>
  <div class="executive-committee">
    <h3>Executive Committee Members</h3>
    <ul>
      {#each execCommitteeMembers as member}
        <li>{member.name}</li>
      {/each}
    </ul>
  </div>
  <div class="ceo-contact">
    <h3>Contact CEO's Office</h3>
    <p>Please contact the CEO's office at:</p>
    <p>Email: <a href="mailto:ceo@company.com">ceo@company.com</a></p>
    <p>Phone: 555-555-5555</p>
  </div>
  <div class="committee-description">
    <h3>Committee Descriptions</h3>
    <ul>
      {#each committees as committee}
        <li>
          <h4>{committee.name}</h4>
          <p>{committee.description}</p>
        </li>
      {/each}
    </ul>
  </div>
  <div class="mailing-list">
    <h3>Sign up for Committees Mailing List</h3>
    <form on:submit|preventDefault={addEmail}>
      <label>
        Email:
        <input type="email" bind:value={email} required />
      </label>
      <button type="submit">Subscribe</button>
    </form>
    {#if subscribed}
      <p>Thank you for subscribing!</p>
    {/if}
  </div>
</div>
<script>
  let boardMembers = [
    { name: "John Smith" },
    { name: "Jane Doe" },
    { name: "Bob Johnson" }
  ];

  let execCommitteeMembers = [
    { name: "Sarah Lee" },
    { name: "Mike Brown" },
    { name: "Emily Davis" }
  ];

  let committees = [
    { name: "Finance Committee", description: "Responsible for managing the organization's finances and budget." },
    { name: "Policy Committee", description: "Responsible for developing and recommending policies related to public transportation." },
    { name: "Safety Committee", description: "Responsible for promoting and maintaining safety in public transportation." }
  ];

  let email = "";
  let subscribed = false;

  function addEmail() {
    subscribed = true;
  }
</script>
<style>
  .container {
    display: flex;
    flex-wrap: wrap;
    gap: 2rem;
    justify-content: center;
    align-items: center;
    padding: 2rem;
    margin: 2rem auto;
    max-width: 1200px;
  }

  .card {
    width: 300px;
    height: 350px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 5px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
    transition: transform 0.3s ease;
  }

  .card:hover {
    transform: translateY(-10px);
  }

  .card-header {
    background-color: #f3f4f6;
    width: 100%;
    height: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    border-top-left-radius: 5px;
    border-top-right-radius: 5px;
  }

  .card-header img {
    max-width: 100%;
    max-height: 100%;
  }

  .card-body {
    padding: 1rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 50%;
    width: 100%;
    background-color: #ffffff;
    border-bottom-left-radius: 5px;
    border-bottom-right-radius: 5px;
  }

  h4 {
    font-size: 1.5rem;
    font-weight: bold;
    margin-bottom: 0.5rem;
  }

  p {
    font-size: 1rem;
    text-align: center;
    margin-bottom: 1rem;
  }

  button {
    background-color: #2563eb;
    color: #ffffff;
    border: none;
    border-radius: 5px;
    padding: 0.5rem 1rem;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  button:hover {
    background-color: #1e40af;
  }
</style>
