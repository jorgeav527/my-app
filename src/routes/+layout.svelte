<script lang="ts">
	import '../app.css';
	import Header from './header.svelte';
	import Footer from './footer.svelte';
</script>


<div class="">
	<Header />
	<!-- Main Content -->
	<main class="flex-grow p-8">
		<slot />
	</main>
	<!-- Main Content -->
	<Footer />
</div>
