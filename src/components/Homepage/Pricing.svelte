<script lang="ts">
	import { onMount } from 'svelte';
	import ToggleSwitch from '../../UI/ToggleSwitch.svelte';
	import PricePlanWidget from '../../UI/PricePlanWidget.svelte';
	import LoadingSkeleton from '../../UI/LoadingSkeleton.svelte';

	let packageName = 'Monthly';
	let isLoading = false;
	let priceData = [
		{
			title: 'Starter',
			price: 29,
			isPopular: false,
			featuresIncluded: [
				{ isIncluded: true },
				{ isIncluded: false },
				{ isIncluded: false },
				{ isIncluded: false }
			]
		},
		{
			title: 'Pro',
			price: 199,
			isPopular: true,
			featuresIncluded: [
				{ isIncluded: true },
				{ isIncluded: true },
				{ isIncluded: false },
				{ isIncluded: false }
			]
		},
		{
			title: 'Platinium',
			price: 599,
			isPopular: false,
			featuresIncluded: [
				{ isIncluded: true },
				{ isIncluded: true },
				{ isIncluded: true },
				{ isIncluded: true }
			]
		}
	];

	onMount(() => {
		fetchPriceData();
	});

	const fetchPriceData = async () => {
		try {
			isLoading = true;
			const response = await fetch('https://n8n.thearc.dev/webhook/pricing', {
				method: 'POST',
				headers: {},
				body: JSON.stringify({ interval: packageName.toLowerCase() })
			});

			if (!response.ok) {
				isLoading = false;
				throw new Error('Failed to fetch data');
			}

			const data = await response.json();
			console.log(data);
			isLoading = false;
			// check if data exist then append that price data into priceData
		} catch (error) {
			isLoading = false;
			console.error(error);
		}
	};

	// function to toggle the switch
	const toggleSwitch = (value: CustomEvent<any>) => {
		packageName = value.detail;
		fetchPriceData();
	};

	const onGetStarted = (data: CustomEvent<any>) => {
		console.log('Get started', data.detail);
	};

	const annualPlan = (data: CustomEvent<any>) => {
		console.log('Annual plan', data.detail);
	};
</script>

<div class="mt-[8rem]">
	<div class="mx-auto md:w-40%">
		<p class="text-2xl text-center">Design For Business Teams like Yours</p>
		<p class=" text-center mt-3">
			Here at flowbite we focus on markets where technology, innovation, and capital can unlock
			long-term value and drive economic growth.
		</p>

		<div class="flex flex-1 justify-center mt-5">
			<ToggleSwitch
				bind:value={packageName}
				label=""
				options={['Monthly', 'Yearly']}
				fontSize={12}
				on:toggleSwitch={toggleSwitch}
			/>
		</div>
	</div>

	<div class="grid grid-cols-1 md:grid-cols-3 gap-10 mt-15 items-end">
		{#each priceData as price}
			<div>
				{#if isLoading}
					<LoadingSkeleton />
				{:else}
					<PricePlanWidget
						title={price.title}
						price={price.price}
						isPopular={price.isPopular}
						featuresIncluded={price.featuresIncluded}
						on:getStarted={onGetStarted}
						on:annualPlan={annualPlan}
					/>
				{/if}
			</div>
		{/each}
	</div>
</div>
