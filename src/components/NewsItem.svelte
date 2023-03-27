<script>
  export let title;
  export let content;
</script>
<style>
/* News Item */
.border-2 {
  border-width: 2px;
}

.rounded-lg {
  border-radius: 0.5rem;
}

.p-4 {
  padding: 1rem;
}

.mb-4 {
  margin-bottom: 1rem;
}

.text-lg {
  font-size: 1.125rem;
  line-height: 1.75rem;
}

.font-bold {
  font-weight: 700;
}

.mb-2 {
  margin-bottom: 0.5rem;
}

.text-gray-600 {
  color: #718096;
}

</style>
<div class="border-2 rounded-lg p-4 mb-4">
  <h2 class="text-lg font-bold mb-2">{title}</h2>
  <p class="text-gray-600">{content}</p>
</div>
