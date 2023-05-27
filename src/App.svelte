<script lang="ts">
  // pages
  import Home from "./pages/Home.svelte";

  // svelte-query
  import { QueryClient, QueryClientProvider } from '@sveltestack/svelte-query';

  // Create a client
  const queryClient = new QueryClient();
</script>

<QueryClientProvider client={queryClient}>
  <Home />
</QueryClientProvider>