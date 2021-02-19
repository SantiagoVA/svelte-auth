<script>
	import Login from "../components/Login.svelte";
	import { currentUser } from "../stores/user.js"
</script>

<style>
	.section1{
		width: 100%;
		min-height: 100vh;
		background-color: #923cb5;
		background-image: linear-gradient(147deg, #923cb5 0%, #000000 74%);
	}

	.container-main{
		position: relative;
		top: 100px;
	}

	h1 {
		font-size: 2.8em;
		font-weight: 700;
		background-color: #2d3436;
		background-image: linear-gradient(315deg, #2d3436 0%, #d3d3d3 74%);
		-webkit-background-clip: text;
  		-webkit-text-fill-color: transparent;
		text-align: center;
		margin: 0;
	}

	h2 {
		color: #d3d3d3;
		position: relative;
		text-align: center;
	}

	footer{
		position: absolute;
		top: 90vh;
		left: 0;
		right: 0;
		bottom: 0;
		margin: auto;
	}

	.img-container{
		display: flex;
		justify-content: center;
		margin: 10px 0;
	}

	img {
		width: 100px;
		border-radius: 50%;
	}

	p {
		color: #d3d3d3;
		text-align: center;
		position: relative;
		top: 20px;
		font-size: 20px;
	}


	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}
</style>

<svelte:head>
	<title>Login</title>
</svelte:head>


<section class="section1">
	<div class="container-main">
	<h1>Welcome {#if $currentUser}{$currentUser.displayName}{/if}! </h1>
{#if $currentUser}
<div class="img-container">
<img src={$currentUser.photoURL} alt="">
</div>
{/if}

<Login />
{#if $currentUser}
<p>   Thanks {$currentUser.displayName} for test this site. <br>
The technologies that was used here is: <br>
<li>
	Svelte
</li>
<li>
	Sapper
</li>
<li>
	Firebase
</li>
</p>
	{/if}



	</div>


<footer>
	<h2>Created by <a href="https://github.com/SantiagoVA" target=_blank>Santiago Vásquez</a> </h2>
</footer>
</section>
