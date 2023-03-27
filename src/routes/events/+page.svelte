<script>
  let events = [
    {
      id: 1,
      title: "First Event",
      date: "2022-04-01",
      description: "This is the description of the first event.",
      attendees: ["John Doe", "Jane Doe"],
    },
    {
      id: 2,
      title: "Second Event",
      date: "2022-05-01",
      description: "This is the description of the second event.",
      attendees: ["Bob Smith"],
    },
    {
      id: 3,
      title: "Third Event",
      date: "2022-06-01",
      description: "This is the description of the third event.",
      attendees: [],
    },
  ];

  let selectedEvent = null;
  let showForm = false;

  function joinEvent(event) {
    selectedEvent = event;
    showForm = true;
  }

  function submitForm() {
    // Handle form submission
  }
</script>

<div class="flex flex-col">
  <h2 class="text-xl font-semibold mb-4">Past Events</h2>
  {#each events as event}
    <div class="flex mb-4">
      <div class="mr-4">
        <div class="text-3xl font-semibold">{event.date.slice(8)}</div>
        <div class="text-sm">{event.date.slice(0, 7)}</div>
      </div>
      <div class="flex-1">
        <div class="text-lg font-semibold">{event.title}</div>
        <div class="text-sm">{event.description}</div>
        <div class="text-sm mt-2">Attendees: {event.attendees.join(", ") || "None"}</div>
        {#if event.id === events[0].id}
          <button on:click={() => joinEvent(event)} class="mt-2 px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-700">
            Join Event
          </button>
        {/if}
      </div>
    </div>
  {/each}
</div>

{#if showForm}
  <div class="flex flex-col">
    <h2 class="text-xl font-semibold mb-4">Join {selectedEvent.title}</h2>
    <form on:submit|preventDefault="{submitForm}">
      <div class="mb-4">
        <label for="name" class="block font-semibold mb-2">Name</label>
        <input type="text" id="name" name="name" required class="w-full border border-gray-300 p-2 rounded focus:outline-none focus:ring-2 focus:ring-blue-500" />
      </div>
      <div class="mb-4">
        <label for="email" class="block font-semibold mb-2">Email</label>
        <input type="email" id="email" name="email" required class="w-full border border-gray-300 p-2 rounded focus:outline-none focus:ring-2 focus:ring-blue-500" />
      </div>
      <button type="submit" class="bg-blue-500 text-white rounded hover:bg-blue-700 px-4 py-2">Join</button>
    </form>
  </div>
{/if}
<style>
.page-container {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  padding: 1rem;
}

.event-list {
  list-style: none;
  padding: 0;
  margin: 0;
  width: 100%;
}

.event-list li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem;
  border-bottom: 1px solid #ccc;
  width: 100%;
  cursor: pointer;
}

.event-list li:hover {
  background-color: #f0f0f0;
}

.event-list li:last-child {
  border-bottom: none;
}

.event-details {
  padding: 1rem;
  background-color: #f0f0f0;
  width: 100%;
  margin-top: 1rem;
}

.join-event-btn {
  background-color: #1e90ff;
  color: #fff;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 0.25rem;
  font-size: 1rem;
  cursor: pointer;
  margin-top: 1rem;
}

.join-event-form {
  display: none;
  padding: 1rem;
  background-color: #f0f0f0;
  width: 100%;
  margin-top: 1rem;
}

.join-event-form.show {
  display: block;
}
</style>