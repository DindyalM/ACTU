<script>
  import { onMount } from 'svelte';
  import NewsItem from '../../components/NewsItem.svelte';

  let newsItems = [];

  onMount(async () => {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts?_limit=3');
    newsItems = await res.json();
  });
</script>
<style>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 2rem;
}

h1 {
  font-size: 2.5rem;
  font-weight: bold;
  margin-bottom: 1.5rem;
}

p {
  font-size: 1.2rem;
}

.news-item {
  display: flex;
  flex-direction: column;
  margin-bottom: 2rem;
  border: 1px solid #ccc;
  padding: 1rem;
  border-radius: 0.25rem;
  width: 80%;
}

.news-item h2 {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.news-item p {
  margin-bottom: 0.5rem;
}

</style>
<main class="container mx-auto px-4 py-8">
 <div class="container">
  <h1>Latest News</h1>
  {#if newsItems.length === 0}
    <p>Loading...</p>
  {:else}
    {#each newsItems as newsItem}
      <NewsItem
        title={newsItem.title}
        content={newsItem.body}
        key={newsItem.id}
      />
    {/each}
  {/if}
</div>

<div class="container">
  <h1>Videos & Interviews</h1>
  {#if newsItems.length === 0}
    <p>Loading...</p>
  {:else}
    {#each newsItems as newsItem}
      <NewsItem
        title={newsItem.title}
        content={newsItem.body}
        key={newsItem.id}
      />
    {/each}
  {/if}
</div>

</main>

