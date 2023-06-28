<script>
	import { browser } from '$app/environment';
	import Button from '../../components/Button.svelte';

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

<div class="flex items-center justify-center">
	<Button on:click={() => count++}>
		Clicked {count}
		{count === 1 ? 'time' : 'times'}
	</Button>

	<Button on:click={getValue}>Adjust max value</Button>
	<Button on:click={() => (count = 0)}>Reset button to 0</Button>
</div>
