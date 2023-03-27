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

<div class="page">
  <h2 class="title">Past Events</h2>
  <div class="events-list">
    <div class="event">
      <div class="event-info">
        <h3 class="event-title">Event Title 1</h3>
        <p class="event-date">Date: May 5, 2023</p>
        <p class="event-description">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
      </div>
      <div class="event-actions">
        <button class="event-media-btn">View Past Event Media</button>
        <button id="join-btn" class="event-join-btn">Join Event</button>
      </div>
    </div>
    <div class="event">
      <div class="event-info">
        <h3 class="event-title">Event Title 2</h3>
        <p class="event-date">Date: December 31, 2022</p>
        <p class="event-description">Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium.</p>
      </div>
      <div class="event-actions">
        <button class="event-join-btn disabled">Join Event</button>
        <button class="event-media-btn">View Past Event Media</button>
        
      </div>
    </div>
    <div class="event">
      <div class="event-info">
        <h3 class="event-title">Event Title 3</h3>
        <p class="event-date">Date: November 30, 2022</p>
        <p class="event-description">Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
      </div>
      <div class="event-actions">
        <button class="event-join-btn disabled">Join Event</button>
        <button class="event-media-btn">View Past Event Media</button>
      </div>
    </div>
  </div>
  <div class="join-form hidden">
    <h3 class="form-title">Join Event</h3>
    <form class="form">
      <label class="form-label" for="name-input">Name:</label>
      <input class="form-input" type="text" id="name-input" name="name" required>
      <label class="form-label" for="email-input">Email:</label>
      <input class="form-input" type="email" id="email-input" name="email" required>
      <label class="form-label" for="message-input">Message:</label>
      <textarea class="form-input" id="message-input" name="message" rows="3" required></textarea>
      <button class="submit-btn" type="submit">Submit</button>
    </form>
  </div>
</div>

<style>
.page {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
}

.title {
  font-size: 2rem;
  margin-bottom: 2rem;
}

.events-list {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
  width: 100%;
}

.event {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 2rem;
  background-color: #f5f5f5;
  box-shadow: 0 0.125rem 0.25rem rgba(0, 0, 0, 0.1);
}

.event-info {
  width: 100%;
  margin-bottom: 1.5rem;
}

.event-title {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
}

.event-date, .event-description {
  margin-bottom: 0.5rem;
}

.event-actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

.event-join-btn, .event-media-btn {
  font-size: 1rem;
  font-weight: bold;
  padding: 1rem;
  border: none;
  border-radius: 0.25rem;
  cursor: pointer;
  transition: background-color 0.2s ease-in-out, color 0.2s ease-in-out;
}

.event-join-btn.disabled {
  background-color: #ccc;
  color: #888;
  cursor: not-allowed;
}

.event-join-btn:hover, .event-media-btn:hover {
  background-color: #1e90ff;
  color: #fff;
}

.join-form {
  display: none;
  margin-top: 2rem;
  width: 100%;
  max-width: 30rem;
}

.form-title {
  font-size: 1.5rem;
  margin-bottom: 1rem;
}

.form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.form-label {
  font-size: 1rem;
}

.form-input, .form-textarea {
  font-size: 1rem;
  padding: 0.5rem;
  border: none;
  border-radius: 0.25rem;
  box-shadow: 0 0.125rem 0.25rem rgba(0, 0, 0, 0.1);
}

.form-textarea {
  resize: vertical;
}

.submit-btn {
  font-size: 1rem;
  font-weight: bold;
  padding: 1rem;
  border: none;
  border-radius: 0.25rem;
  background-color: #1e90ff;
  color: #fff;
  cursor: pointer;
  transition: background-color 0.2s ease-in-out, color 0.2s ease-in-out;
}

.submit-btn:hover {
  background-color: #0077b6;
  color: #fff;
}
</style>
