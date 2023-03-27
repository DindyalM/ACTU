<script>
let threads = [
  {
    "title": "Administrative",
    "topics": [
      {
        "title": "Board of Committee ",
        "posts": [
          {
            "author": "User A",
            "message": "This is the first post.",
            "comments": [
              {
                "author": "User B",
                "message": "This is a comment on the first post."
              }
            ]
          },
          {
            "author": "User C",
            "message": "This is the second post.",
            "comments": [
              {
                "author": "User D",
                "message": "This is a comment on the second post."
              }
            ]
          }
        ]
      },
      {
        "title": "Governance Committee",
        "posts": [
          {
            "author": "User E",
            "message": "This is the first post for Topic 2.",
            "comments": [
              {
                "author": "User F",
                "message": "This is a comment on the first post for Topic 2."
              }
            ]
          }
        ]
      },
      {
        "title": "Audit Committee",
        "posts": [
          {
            "author": "User E",
            "message": "This is the first post for Topic 2.",
            "comments": [
              {
                "author": "User F",
                "message": "This is a comment on the first post for Topic 2."
              }
            ]
          }
        ]
      },
      {
        "title": "Nominating Committee",
        "posts": [
          {
            "author": "User E",
            "message": "This is the first post for Topic 2.",
            "comments": [
              {
                "author": "User F",
                "message": "This is a comment on the first post for Topic 2."
              }
            ]
          }
        ]
      },{
        "title": "Regional Chairs Committee",
        "posts": [
          {
            "author": "User E",
            "message": "This is the first post for Topic 2.",
            "comments": [
              {
                "author": "User F",
                "message": "This is a comment on the first post for Topic 2."
              }
            ]
          }
        ]
      },{
        "title": "Executive Committee",
        "posts": [
          {
            "author": "User E",
            "message": "This is the first post for Topic 2.",
            "comments": [
              {
                "author": "User F",
                "message": "This is a comment on the first post for Topic 2."
              }
            ]
          }
        ]
      }
    ]
  },
  {
    "title": "Regional Committees",
    "topics": [
      {
        "title": "Topic 1",
        "posts": [
          {
            "author": "User G",
            "message": "This is the first post for Topic 1.",
            "comments": [
              {
                "author": "User H",
                "message": "This is a comment on the first post for Topic 1."
              }
            ]
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

  function selectTopic(topic) {
    selectedTopic = topic;
  }

  function createPost() {
    selectedTopic.posts.push({
      id: selectedTopic.posts.length + 1,
      author: 'User X',
      message: 'This is a new post.',
      comments: []
    });
  }

  function createComment(post) {
    post.comments.push({
      id: post.comments.length + 1,
      author: 'User Y',
      message: 'This is a new comment.'
    });
  }

  function showCommentBox(post) {
  post.showCommentBox = !post.showCommentBox;
}

</script>
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
        <div class="border border-gray-200 rounded p-4 my-2" key={post.id}>
          <p class="text-gray-600 mb-2">{post.author}</p>
          <p class="text-lg mb-2">{post.message}</p>
          <div class=comment>
          <div class="ml-4">
            {#each post.comments as comment}
              <div class="border border-gray-200 rounded p-2 my-2" key={comment.id}>
                <p class="text-gray-600 mb-2">{comment.author}</p>
                <p>{comment.message}</p>
              </div>
            {/each}
          </div>
          </div>
          <div class="mt-4">
            <button class="bg-gray-200 py-2 px-4 rounded-lg" on:click={() => showCommentForm(post)}>
              Comment
            </button>
          </div>
          {#if showCommentBox === post.id}
            <div class="mt-4">
              <textarea
                class="border border-gray-200 rounded p-2 w-full"
                rows="3"
                on:input={(e) => updateComment(e, post)}
              ></textarea>
              <div class="flex justify-end mt-2">
                <button class="bg-blue-500 text-white py-2 px-4 rounded-lg" on:click={() => saveComment(post)}>
                  Save
                </button>
              </div>
            </div>
          {/if}
        </div>
      {/each}
    </div>
  {/each}
</div>
<style>
  .container {
    max-width: 600px;
    margin: 0 auto;
    padding: 0 1rem;
  }
  
  h1 {
    font-size: 1.5rem;
    font-weight: bold;
    margin: 2rem 0;
  }
  
  .thread {
    margin-bottom: 2rem;
  }
  
  .topic {
    margin-bottom: 1rem;
    font-weight: bold;
    font-size: 1.2rem;
  }
  
  .post {
    margin-bottom: 1rem;
    padding: 1rem;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  .post-author {
    font-weight: bold;
    margin-bottom: 0.5rem;
  }
  
  .post-message {
    margin-bottom: 0.5rem;
  }
  
  .comment {
    margin-bottom: 0.5rem;
    padding: 0.5rem;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f7f7f7;
  }
  
  .comment-author {
    font-weight: bold;
    margin-bottom: 0.25rem;
  }
  
  .comment-message {
    margin-bottom: 0.25rem;
  }
</style>
