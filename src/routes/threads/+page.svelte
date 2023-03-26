<!-- src/routes/threads/+page.svelte -->
<div class="container mx-auto my-4">
  <h1 class="text-2xl font-bold mb-4">{selectedThread.title}</h1>

  <nav class="flex justify-between mb-4">
    <ul class="flex space-x-4">
      {#each threads as thread}
        <li class="cursor-pointer" on:click={() => selectThread(thread)} key={thread.id}>
          {thread.title}
        </li>
      {/each}
    </ul>
    <button class="px-4 py-2 bg-blue-500 text-white rounded-lg" on:click={createPost}>
      Create Post
    </button>
  </nav>

  {#each selectedThread.topics as topic}
    <div class="border-b border-gray-400 py-2 mb-4" key={topic.id}>
      <h2 class="font-bold">{topic.title}</h2>
      {#each topic.posts as post}
        <div class="border-b border-gray-200 py-2 mt-2" key={post.id}>
          <p class="text-gray-600 mb-2">{post.author}</p>
          <p>{post.message}</p>
        </div>
      {/each}
    </div>
  {/each}
</div>

<script>
  let threads = [
  {
    "id": 1,
    "title": "General Document",
    "topics": [
      {
        "id": 1,
        "title": "AGM",
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
        "title": "Annual Reports",
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
        "title": "By-Laws",
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
    ]
  },
  {
    "id": 2,
    "title": "Committees",
    "topics": [
      {
        "id": 1,
        "title": "Administrative",
        "posts": [
          {
            "id": 1,
            "author": "User I",
            "message": "This is the first post."
          },
          {
            "id": 2,
            "author": "User J",
            "message": "This is the second post."
          }
        ]
      },
      {
        "id": 2,
        "title": "Regional Committees",
        "posts": [
          {
            "id": 1,
            "author": "User K",
            "message": "This is the first post."
          },
          {
            "id": 2,
            "author": "User L",
            "message": "This is the second post."
          },
          {
            "id": 3,
            "author": "User M",
            "message": "This is the third post."
          }
        ]
      }
    ]
  }
];

  
  let selectedThread = threads[0];
  let selectedTopic = selectedThread.topics[0];

  function selectThread(thread) {
    selectedThread = thread;
    selectedTopic = thread.topics[0];
  }

  function createPost() {
    selectedTopic.posts.push({
      id: selectedTopic.posts.length + 1,
      author: 'User X',
      message: 'This is a new post.',
    });
  }
</script>
