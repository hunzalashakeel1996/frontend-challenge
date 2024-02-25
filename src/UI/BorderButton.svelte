<script lang="ts">
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

	const onButtonClick = () => {
		dispatch('click');
	};
</script>

<button
	on:click={onButtonClick}
	class="bg-white hover:bg-gray-100 text-gray-800 py-2 px-4 border border-gray-400 rounded shadow"
	><slot />
</button>
