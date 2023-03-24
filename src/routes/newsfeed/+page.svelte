<script>
  import { onMount } from 'svelte';
  import NewsItem from '../../components/NewsItem.svelte';

  let newsItems = [];

  onMount(async () => {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts');
    newsItems = await res.json();
  });
</script>

<main class="container mx-auto px-4 py-8">
  <h1 class="text-3xl font-bold mb-8">Latest News</h1>
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
</main>

