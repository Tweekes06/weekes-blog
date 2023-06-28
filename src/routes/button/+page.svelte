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

<h1 class="text-5xl mb-8">The button</h1>

<button class="m-1 px-2 py-1 bg-blue-500 rounded" on:click={() => count++}>
	Clicked {count}
	{count === 1 ? 'time' : 'times'}
</button>

<button class="m-1 px-2 py-1 bg-blue-500 rounded" on:click={getValue}> Adjust max value </button>
<button class="m-1 px-2 py-1 bg-blue-500 rounded" on:click={() => (count = 0)}
	>Reset button to 0</button
>
