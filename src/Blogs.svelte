<script>
  import CardLayout from "./components/CardLayout.svelte";
  import CardItem from "./components/CardItem.svelte";
  import Overlay from "./components/Overlay.svelte";
  import { ApolloClient, InMemoryCache, gql } from "@apollo/client";
  import { setClient, query } from "svelte-apollo";
  import Pagination from './components/Pagination.svelte'

  const client = new ApolloClient({
    cache: new InMemoryCache(),
    uri: "https://d33ip4f514s3iy.cloudfront.net/cms/read/en-US",
    headers: {
      Authorization: `Bearer a65bc94d4d3ae90711af1c46491d33c2dbe2a8ff15c9c8f2`,
    },
  });
  setClient(client);

  const GET_BLOGS = gql`
    query getBlogs($limit: Int, $cursor: String) {
      listBlogs(limit: $limit, after: $cursor) {
        data {
          title
          coverImage
          content
        }
        meta {
          cursor
          hasMoreItems
        }
      }
    }
  `;

  // let cursors = [];
  // let page = writable(0);
  // let currentPage = 0;

  const blogs = query(GET_BLOGS, {
    variables: {
      limit: 2,
    },
  });

  const {fetchMore} = blogs;


  // const pageInfo = blogs.data.listBlogs?.meta;
  // console.log($blogs.data.listBlogs.data.length);

</script>

<main>
  {#if $blogs.loading}
    <Overlay />
  {:else}
    <div class="container">
      <CardLayout>
        {#each $blogs.data.listBlogs.data as item}
          <CardItem {item} />
        {/each}
      </CardLayout>
    </div>
  {/if}

  {#if !$blogs.loading}
    <Pagination onLoadMore="{() => {
        if ($blogs.data.listBlogs.meta.hasMoreItems) {
          fetchMore({
            variables: {
              cursor: $blogs.data.listBlogs.meta.cursor,
            },
          });
        }
      }}"
      />
    
  {/if}
</main>