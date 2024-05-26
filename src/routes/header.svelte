<script lang="ts">
    import * as config from '$lib/config';
    import { goto } from '$app/navigation';
</script>

<!-- Header -->
<nav class="bg-gray-800 p-4">
    <div class="container mx-auto flex justify-between items-center">
        <a href="/" class="text-white text-xl font-bold">Portfolio</a>
        <div class="space-x-4">
            <button on:click={() => goto('/about')} class="text-gray-300 hover:text-white">About</button>
            <button on:click={() => goto('/contact')} class="text-gray-300 hover:text-white">Contact</button>
            <button on:click={() => goto('/projects')} class="text-gray-300 hover:text-white">Projects</button>
            <button on:click={() => goto('/thoughts')} class="text-gray-300 hover:text-white">Thoughts</button>
        </div>
    </div>
</nav>
<!-- Header -->