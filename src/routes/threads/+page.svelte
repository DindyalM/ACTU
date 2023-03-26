<!-- src/routes/threads/+page.svelte -->
<div class="container mx-auto my-4">
  <h1 class="text-2xl font-bold mb-4">{thread.title}</h1>

  <nav class="flex justify-between mb-4">
    <ul class="flex space-x-4">
      {#each threads as thread}
        <li class="cursor-pointer" key={thread.id}>
          {thread.title}
        </li>
      {/each}
    </ul>
    <button class="px-4 py-2 bg-blue-500 text-white rounded-lg" on:click={createPost}>
      Create Post
    </button>
  </nav>

  {#each thread.posts as post}
    <div class="border-b border-gray-400 py-2 mb-4" key={post.id}>
      <h2 class="font-bold">{post.author}</h2>
      <p>{post.message}</p>
    </div>
  {/each}
</div>

<script>
  let threads = [
    {
      "id": 1,
      "title": "Thread 1",
      "posts": [
        {
          "id": 1,
          "author": "User A",
          "message": "This is the first post."
        },
        {
          "id": 2,
          "author": "User B",
          "message": "This is the second post."
        },
        {
          "id": 3,
          "author": "User C",
          "message": "This is the third post."
        }
      ]
    },
    {
      "id": 2,
      "title": "Thread 2",
      "posts": [
        {
          "id": 1,
          "author": "User D",
          "message": "This is the first post."
        },
        {
          "id": 2,
          "author": "User E",
          "message": "This is the second post."
        }
      ]
    },
    {
      "id": 3,
      "title": "Thread 3",
      "posts": [
        {
          "id": 1,
          "author": "User F",
          "message": "This is the first post."
        },
        {
          "id": 2,
          "author": "User G",
          "message": "This is the second post."
        },
        {
          "id": 3,
          "author": "User H",
          "message": "This is the third post."
        }
      ]
    }
  ];

  let thread = threads[0];

  function createPost() {
    thread.posts.push({
      id: thread.posts.length + 1,
      author: 'User X',
      message: 'This is a new post.',
    });
  }
</script>
