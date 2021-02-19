<script>
	import UserObserver from '../components/userObserver.svelte';
</script>

<style>
	main {
		position: relative;
		background-color: white;
		padding: 0;
		margin: 0;
		box-sizing: border-box;
	}
</style>
<UserObserver/>


<main>
	<slot></slot>
</main>