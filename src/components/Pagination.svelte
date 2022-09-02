<script>
  // import { createEventDispatcher } from 'svelte'

  // const dispatch = createEventDispatcher()

  // export let page;
  // export let currentPage;
  // export let condition;
  export let onLoadMore;

  // function handleOptionClick (option) {
  //   if (option !== currentPage){
  //     dispatch('setPage', option)
  //   }
  // }
</script>



  <div class="next-prev">
    <!-- <button
      disabled={currentPage <= 1}
      style={{ backgroundColor: `${currentPage <= 1 ? "gray" : "#6796ec"}` }}
      on:click="{() => handleOptionClick(currentPage - 1)}"
    >
      Prev
    </button
    > -->
    <button
      class="active"
      
      on:click="{onLoadMore}"
      >
        Next
      </button
    >
  </div>

  <!-- style={{
        backgroundColor: `${
          condition ? "#6796ec" : "gray"
        }`,
      }} -->