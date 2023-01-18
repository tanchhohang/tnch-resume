<script>
	// export let name;
	import Navbar from './components/navbar.svelte';
	import Gallery from './components/gallery.svelte';
  	import Foot from './components/foot.svelte';
</script>

<header>
	<Navbar/>
</header>

<main>
	<Gallery/>
</main>

<footer>
	<Foot/>
</footer>

<style>
	main {
		text-align: center;
		padding: 0.5rem;
		margin: 0 auto;
	}

	footer {
		padding: 20px;
		background-color: #000;
	}
</style>