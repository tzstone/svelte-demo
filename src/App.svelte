<script lang="ts">
	import Outer from './Outer.svelte'
	export let name: string;
	let age = 18
	// 变量
	$: doubled = age * 2
	// 代码块
	$: {
		console.log('cur age', age)
	}
	// if 代码块
	$: if (age > 20) {
		console.log('more then 20')
	}

	function addAge() {
		age+=1;
	}

	let cats = [
		{ id: 'J---aiyznGQ', name: 'Keyboard Cat' },
		{ id: 'z_AbfPXTKms', name: 'Maru' },
		{ id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' }
	];

	let promise = new Promise((resolve, reject) => {
		setTimeout(() => {
			resolve(111)
		}, 1000);
	})

	let m = { x: 0, y: 0 };

	function handleMessage(e) {
		alert(e.detail.text)
	}

	function handleClick(e) {
		alert('clicked');
	}
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>age {age}</p>
	<p>doubled age {doubled}</p>
	{#if age > 20}
		<p>more then 20</p>
	{/if}
	<button on:click={addAge}>addAge</button>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

	<ul>
		{#each cats as { id, name }, i}
			<li><a target="_blank" href="https://www.youtube.com/watch?v={id}">
				{i + 1}: {name}
			</a></li>
		{/each}
	</ul>

	{#await promise}
		<p>waiting</p>
	{:then number} 
		<p>number is {number}</p>
	{:catch error}
		<p>error: {error}</p>
	{/await}

	{#await promise then number}
		<p>number is {number}</p>
	{/await}

	<div on:mousemove="{e => m = { x: e.clientX, y: e.clientY }}">
		The mouse position is {m.x} x {m.y}
	</div>
</main>

<Outer on:message='{handleMessage}' on:click='{handleClick}'></Outer>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: blue;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>