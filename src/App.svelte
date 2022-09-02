<script>
  import Blogs from "./Blogs.svelte";
	import Header from "./components/Header.svelte";
	import NewContent from './Content.svelte'
  // import ApolloClient, {InMemoryCache }  from "apollo-boost";
  // import { setClient } from "svelte-apollo";

  // const client = new ApolloClient({
  //   cache: new InMemoryCache(),
  //   uri: "https://d33ip4f514s3iy.cloudfront.net/cms/read/en-US",
	// 	request: operation => {
	// 		const token = "a65bc94d4d3ae90711af1c46491d33c2dbe2a8ff15c9c8f2"
	// 		operation.setContext({
	// 			headers: {
	// 				authorization: token ? `Bearer ${token}` : '', 
	// 			},
	// 		});
	// 	},
  // });
  // setClient(client);
</script>

<main>
	<Header />
	<NewContent />
  <Blogs />
</main>