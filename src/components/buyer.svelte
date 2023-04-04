<!-- BuyersGuide.svelte -->

<script>
  import { onMount } from 'svelte';

  // Define the product data structure
  const products = [
    {
      id: 1,
      name: 'Product 1',
      description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
      price: 9.99,
      rating: 4.5,
      image: 'https://picsum.photos/200/300'
    },
    {
      id: 2,
      name: 'Product 2',
      description: 'Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
      price: 19.99,
      rating: 3.5,
      image: 'https://picsum.photos/200/300'
    },
    {
      id: 3,
      name: 'Product 3',
      description: 'Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
      price: 29.99,
      rating: 5.0,
      image: 'https://picsum.photos/200/300'
    },
  ];

  let filteredProducts = [];
  let searchTerm = '';

  function handleSearch(event) {
    const { value } = event.target;
    searchTerm = value;
    filteredProducts = products.filter(product => product.name.toLowerCase().includes(searchTerm.toLowerCase()) || product.description.toLowerCase().includes(searchTerm.toLowerCase()));
  }

  function clearSearch() {
    searchTerm = '';
    filteredProducts = products;
  }

  onMount(() => {
    // Populate list of products
    filteredProducts = products;
  });
</script>

<div class="flex flex-col items-center">
  <h1 class="text-3xl font-bold my-4">Buyer's Guide</h1>

  <form>
    <label class="block my-4">
      <span class="text-gray-700">Search:</span>
      <input type="text" class="form-input mt-1 block w-full" on:input={handleSearch}>
    </label>
  </form>

  {#if filteredProducts.length === 0}
    <p class="text-gray-700 my-4">No products found.</p>
  {:else}
    <ul class="my-4">
      {#each filteredProducts as product}
        <li class="my-4 flex">
          <img class="w-1/4" src={product.image} alt={product.name} />
          <div class="w-3/4 ml-4">
            <h2 class="font-bold text-xl">{product.name}</h2>
            <p class="text-gray-700 my-2">{product.description}</p>
            <p class="text-gray-700 my-2">${product.price.toFixed(2)}</p>
            <p class="text-gray-700 my-2">{product.rating} stars</p>
          </div>
        </li>
      {/each}
    </ul>
  {/if}

  <button class="px-2 py-1 rounded bg-gray-200 hover:bg-gray-300 focus:outline-none" on:click={clearSearch}>Clear Search</button>
</div>
