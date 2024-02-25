<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	export let color = 'bg-blue-500';

	const onButtonClick = () => {
		dispatch('click');
	};
</script>

<button on:click={onButtonClick} class={`${color} hover:bg-blue-700 text-white py-2 px-4 rounded`}>
	<slot />
</button>
