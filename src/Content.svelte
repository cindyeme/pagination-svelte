<script>
  let allContent = ["hi", "bye", "lie", "tie", "fry", "cry", "pie", "my", "guy"];
  let currentPage = 3; // Update this to simulate page change.
  let postsPerPage = 2;
  let allPosts = allContent;
  let totalPosts = allPosts.length;
  let totalPages = Math.ceil(totalPosts / postsPerPage);
  $: postRangeHigh = currentPage * postsPerPage;
  $: postRangeLow = postRangeHigh - postsPerPage;
	const setCurrentPage = newPage => {
		currentPage = newPage;
	}
</script>

{#each allPosts as post, i}
  {#if i >= postRangeLow && i < postRangeHigh}
    <h3>{post}</h3>
  {/if}
{/each}

<ul>
	{#if currentPage > 1}
	  <li><a href="/blog/{currentPage - 1}" on:click|preventDefault={() => setCurrentPage(currentPage - 1)}>previous</a></li>
	{/if}
  <!-- {#each [3,2,1] as i}
    {#if currentPage - i > 0}
      <li><a href="/blog/{currentPage - i}" on:click|preventDefault={() => setCurrentPage(currentPage - i)}>{currentPage - i}</a></li>
    {/if}
  {/each}
  <li><span>{currentPage}</span></li>
  {#each Array(3) as _, i}
    {#if currentPage + (i+1) <= totalPages}
      <li><a href="/blog/{currentPage + (i+1)}" on:click|preventDefault={() => setCurrentPage(currentPage + (i+1))}>{currentPage + (i+1)}</a></li>
    {/if}
  {/each} -->
  {#if currentPage < totalPages}
	  <li><a href="/blog/{currentPage + 1}" on:click|preventDefault={() => setCurrentPage(currentPage + 1)}>next</a></li>
  {/if}
</ul>