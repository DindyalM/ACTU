<header class="bg-gray-900 text-white py-2 px-4">
  <div class="container mx-auto flex justify-between items-center">
    <h1 class="font-bold text-xl">CUTA/ACTU Member</h1>
    <nav>
      <ul class="flex space-x-4">
				<li><a href="/newsfeed" class="hover:text-gray-400">News</a></li>

        <li><a href="/members" class="hover:text-gray-400">Directory</a></li>

        <li><a href="/documents" class="hover:text-gray-400">Documents</a></li>
        <li><a href="/events" class="hover:text-gray-400">Events</a></li>
        <li><a href="/threads" class="hover:text-gray-400">Committees</a></li>
        <li><a href="/factbook" class="hover:text-gray-400">FactBook</a></li>
      </ul>
    </nav>
  </div>
</header>
<style>
body {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

main {
  flex-grow: 1;
}

header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  background-color: #1a202c;
  color: white;
  font-size: 1.2rem;
  font-weight: bold;
}

nav ul {
  display: flex;
  justify-content: center;
  align-items: center;
  list-style-type: none;
}

nav li {
  margin: 0 1rem;
}

nav a {
  color: white;
  text-decoration: none;
  padding: 0.5rem;
  border-radius: 0.5rem;
}

nav a:hover {
  background-color: #4a5568;
}

nav .active {
  background-color: #ef4444;
}

@media only screen and (max-width: 600px) {
  nav ul {
    flex-direction: column;
  }

  nav li {
    margin: 0.5rem 0;
  }
}

</style>