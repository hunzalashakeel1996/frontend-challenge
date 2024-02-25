<script lang="ts">
	import heroElementImage from '../../assets/hero-element.png';
	import FilledButton from '../../UI/FilledButton.svelte';
	import BorderButton from '../../UI/BorderButton.svelte';

	const onLearnMore = () => {
		console.log('Learn more');
	};

	const onWatchVideo = () => {
		console.log('Watch video');
	};
</script>

<div class="grid grid-cols-1 md:grid-cols-3 gap-2">
	<div class="col-span-2 md:ml-10 flex flex-1 flex-col justify-center">
		<p class="text-3xl text-center">We invest in the world's potential</p>
		<p class="text-center mt-5">
			Here at flowbite we focus on markets where technology, innovation, and capital can unlock
			long-term value and drive economic growth.
		</p>
		<div class="flex justify-center space-x-4 mt-8 mb-5">
			<FilledButton on:click={onLearnMore}>Learn more</FilledButton>
			<BorderButton on:click={onWatchVideo}>Watch video</BorderButton>
		</div>
	</div>
	<div class="flex flex-1 justify-center">
		<img src={heroElementImage} class="w-auto h-40 md:h-80" alt="" />
	</div>
</div>
