<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	import FilledButton from '../UI/FilledButton.svelte';
	import creditBlack from '../assets/creditBlack.png';
	import chatBlack from '../assets/chatBlack.png';
	import chatGrey from '../assets/chatGrey.png';
	import featureBlack from '../assets/featureBlack.png';
	import featureGrey from '../assets/featureGrey.png';
	import financeBlack from '../assets/financeBlack.png';
	import financeGrey from '../assets/financeGrey.png';

	interface Feature {
		isIncluded?: boolean;
	}

	export let title: string;
	export let price: number;
	export let isPopular: boolean;
	export let featuresIncluded: Feature[];

	let featureText = [
		'All tools you need to manage payments',
		'Get hundreds of feature updates',
		'Financial reconcilation and reporting',
		'24x7 phone, chat and email support'
	];

	const iconToUsed = (index: number, isIncluded = false) => {
		if (index == 0) return creditBlack;
		else if (index == 1) return isIncluded ? featureBlack : featureGrey;
		else if (index == 2) return isIncluded ? financeBlack : financeGrey;
		else if (index == 3) return isIncluded ? chatBlack : chatGrey;
	};

	const onGetStarted = () => {
		dispatch('getStarted', { price, title });
	};

	const annualPlan = () => {
		dispatch('annualPlan', { price, title });
	};
</script>

<div>
	<div class="p-5 rounded-lg border border-[#d6d6d6] flex flex-1 flex-col justify-center">
		{#if isPopular}
			<p
				class="self-center text-md text-center border w-32 px-1 mb-3 text-blue-600 rounded-lg bg-slate-200"
			>
				Most popular
			</p>
		{/if}
		<p class="text-2xl text-center">{title}</p>
		<p class="text-center mt-3">
			<span class="text-5xl">$</span>
			<span class="text-5xl">{price}</span>
		</p>

		<button class="text-blue self-center mt-4 mb-8" on:click={annualPlan}>Go to annual plan</button>

		<FilledButton color={isPopular ? 'bg-blue-500' : 'bg-black'} on:click={onGetStarted}
			>Get started</FilledButton
		>

		{#each featuresIncluded as feature, index}
			<div class="flex flex-1 mt-5 items-center">
				<img src={iconToUsed(index, feature.isIncluded)} class="w-auto h-3" alt="" />
				<p
					class={`${!feature.isIncluded && 'text-slate-500'} ${
						!feature.isIncluded && 'line-through'
					} ml-2`}
				>
					{featureText[index]}
				</p>
			</div>
		{/each}
	</div>
</div>
