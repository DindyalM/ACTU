<div class="factbook-container">
  <h3>Factbook</h3>
  <div class="buttons">
    <button class={role === 'transit-user' ? 'active' : ''} on:click={setTransitUser}>Transit System User</button>
    <button class={role === 'cuta-staff' ? 'active' : ''} on:click={setCUTAStaff}>CUTA Staff</button>
    <button class={role === 'general-member' ? 'active' : ''} on:click={setGeneralMember}>General Member</button>
  </div>
  <div class="factbook-content">
    <div class="survey-form" style={role !== 'transit-user' ? 'display: none;' : ''}>
      <!-- Integration with Gravity Forms or alternative survey tool -->
      <p>This survey form is accessible only to a select subset of Transit System Users.</p>
    </div>
    <div class="factbook-purchase" style={role !== 'general-member' ? 'display: none;' : ''}>
      <!-- E-commerce functionality for purchasing Factbooks and immediate PDF delivery upon purchase -->
      <p>E-commerce functionality for purchasing Factbooks and immediate PDF delivery upon purchase is restricted to General Members, with Transit System Users receiving it for free.</p>
    </div>
    <div class="data-request" style={role !== 'cuta-staff' ? 'display: none;' : ''}>
      <!-- Integration with Asana or alternative project management tool -->
      <p>Data request form is accessible only to CUTA Staff.</p>
      <p>Follow-up tasks will be created for CUTA Staff upon submission.</p>
    </div>
  </div>
</div>
<script>
  let role = 'transit-user';

  function setTransitUser() {
    role = 'transit-user';
  }

  function setCUTAStaff() {
    role = 'cuta-staff';
  }

  function setGeneralMember() {
    role = 'general-member';
  }
</script>
<style>
.factbook-container {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
}

.factbook-container h3 {
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

.factbook-content {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.survey-form, .factbook-purchase, .data-request {
  margin-top: 2rem;
}

.survey-form p, .factbook-purchase p, .data-request p {
  margin-bottom: 0.5rem;
}

@media (min-width: 768px) {
  .factbook-content {
    flex-direction: row;
  }

  .survey-form, .factbook-purchase, .data-request {
    margin-top: 0;
    margin-left: 2rem;
    margin-right: 2rem;
  }
}
</style>
