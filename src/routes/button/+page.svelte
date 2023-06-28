<script>
	import { browser } from '$app/environment';

	let count = 0;
	let maxValue = null;
	let x = 0;

	function getValue() {
		maxValue = prompt('what is the maximum amount of times the box can be clicked?');
		if (maxValue != null) {
			x = parseInt(maxValue);
			x++;
			count = 0;
		}
	}

	while (maxValue == null && browser) getValue();

	$: if (count == x) {
		if (browser) alert('The button has been pressed too many times');
		count = 0;
	}
</script>

<h1>The button</h1>

<button on:click={() => count++}>
	Clicked {count}
	{count === 1 ? 'time' : 'times'}
</button>

<button on:click={getValue}> Adjust max value </button>
<button on:click={() => (count = 0)}>Reset button to 0</button>
