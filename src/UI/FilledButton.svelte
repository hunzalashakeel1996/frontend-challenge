<script lang="ts">
	export let color = 'bg-blue-500';
</script>

<button class={`${color} hover:bg-blue-700 text-white py-2 px-4 rounded`}>
	<slot />
</button>
