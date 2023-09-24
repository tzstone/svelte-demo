<script>
  let a = 1;
	let b = 2;
	let yes = false
</script>

<label>
	<input type=number bind:value={a} min=0 max=10>
	<input type=range bind:value={a} min=0 max=10>
</label>

<p>{a} + {b} = {a + b}</p>

<label>
	<input type="checkbox" bind:checked={yes}>yes
</label>

<button disabled={!yes}>submit</button>