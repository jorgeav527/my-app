<script lang="ts">
    import * as config from '$lib/config';
    import { goto } from '$app/navigation';
    let isMenuOpen = false;
</script>

<!-- Header -->
<nav class="bg-gray-800 p-4">
    <div class="container mx-auto flex justify-between items-center">
        <a href="/" class="text-white text-xl font-bold">Portfolio</a>
        <div class="hidden md:flex space-x-4">
            <button on:click={() => goto('/about')} class="text-gray-300 hover:text-white">About</button>
            <button on:click={() => goto('/contact')} class="text-gray-300 hover:text-white">Contact</button>
            <button on:click={() => goto('/projects')} class="text-gray-300 hover:text-white">Projects</button>
            <button on:click={() => goto('/thoughts')} class="text-gray-300 hover:text-white">Thoughts</button>
        </div>
        <button class="md:hidden text-gray-300 hover:text-white" on:click={() => isMenuOpen = !isMenuOpen}>
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
            </svg>
        </button>
    </div>
    {#if isMenuOpen}
    <div class="md:hidden mt-2 space-y-2">
        <button on:click={() => { goto('/about'); isMenuOpen = false; }} class="block w-full text-left text-gray-300 hover:text-white">About</button>
        <button on:click={() => { goto('/contact'); isMenuOpen = false; }} class="block w-full text-left text-gray-300 hover:text-white">Contact</button>
        <button on:click={() => { goto('/projects'); isMenuOpen = false; }} class="block w-full text-left text-gray-300 hover:text-white">Projects</button>
        <button on:click={() => { goto('/thoughts'); isMenuOpen = false; }} class="block w-full text-left text-gray-300 hover:text-white">Thoughts</button>
    </div>
    {/if}
</nav>
<!-- Header -->