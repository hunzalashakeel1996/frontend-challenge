<script lang="ts">
	import LegalFeature from '../../assets/LegalFeature.png';
	import BusinessFeature from '../../assets/BusinessFeature.png';
	import MarketingFeature from '../../assets/MarketingFeature.png';

	// object to hold the feature widgets
	let featureWidgets = [
		{
			title: 'Marketing',
			description:
				'Plan it, create it, launch it. Collaborate seamlessly with all the organization and hit your marketing goals every month with our marketing plan.',
			image: MarketingFeature
		},
		{
			title: 'Legal',
			description:
				'Protect your organization, devices and stay compliant with our structured workflows and custom permissions made for you.',
			image: LegalFeature
		},
		{
			title: 'Business Automation',
			description:
				'Auto-assign tasks, send Slack messages, and much more. Now power up with hundreds of new templates to help you get started.',
			image: BusinessFeature
		}
	];
</script>

<div class="mt-[8rem]">
	<p class="text-3xl">Designed for business teams like yours</p>

	<p class="mt-5">
		Here at flowbite we focus on markets where technology, innovation, and capital can unlock
		long-term value and drive economic growth.
	</p>

	<div class="grid grid-cols-1 md:grid-cols-3 gap-3 mt-8">
		{#each featureWidgets as feature}
			<div class="mt-5 md:mt-0">
				<img src={feature.image} class="w-auto h-10" alt="" />
				<p class="font-bold mt-3">{feature.title}</p>
				<p class="mt-1">{feature.description}</p>
			</div>
		{/each}
	</div>
</div>
