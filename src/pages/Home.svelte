<script lang="ts">
    import {useQuery} from '@sveltestack/svelte-query';
    import UserCard from '../lib/UserCard.svelte';

    const apiUrl = import.meta.env.VITE_API_URL;

    const queryResult = useQuery('users', () => fetch(`${apiUrl}/users?limit=12`).then(res => res.json()));
</script>


<h1 class="text-3xl font-bold text-gray-900 px-4 md:px-20 pt-20 mb-5">Users list: </h1>
<main class="grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-3 md:px-20 px-4">
    {#if $queryResult.isLoading}
        <p>Loading...</p>
    {:else if $queryResult.isError}
        <p>Error: Something went wrong!</p>
    {:else if $queryResult.isSuccess}
        {#each $queryResult.data.users as user}
            <UserCard
                user={user}
            />
        {/each}
    {/if}
</main>