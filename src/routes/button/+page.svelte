<script>
	import { parse } from 'svelte/compiler';

	let count = 0;
	let maxValue = null;
	let x = 0;

	function increment() {
		count++;
	}

	while (maxValue == null) {
		maxValue = prompt('what is the maximum amount of times the box can be clicked?');
		if (maxValue != null) {
			x = parseInt(maxValue);
			x = x++;
		}
	}

	$: if (count == x) {
		alert('The button has been pressed too many times');
		count = 0;
	}
</script>

<h1>The button</h1>

<button on:click={increment}>
	Clicked {count}
	{count === 1 ? 'time' : 'times'}
</button>
