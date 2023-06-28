<script>
	let count = 0;

	function increment() {
		count++;
	}

	$: if (count >= 10) {
		alert('The button has been pressed too many times');
		count = 0;
	}
</script>

<h1>The button</h1>

<button on:click={increment}>
	Clicked {count}
	{count === 1 ? 'time' : 'times'}
</button>
