<script lang="ts">
	let email = '';
	let emailError = false;
	let successEmail = false;

	// function to check if the email is valid
	const onSubscribe = () => {
		// if the email is not valid, set emailError to true
		let emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
		if (!email || !emailRegex.test(email)) {
			emailError = true;
			return;
		}
		// else show the success message and reset the emailError
		emailError = false;
		successEmail = true;
		setTimeout(() => {
			successEmail = false;
			email = '';
		}, 3000);
		// send the email to the server for newsletter subscription
	};
</script>

<div class="mt-[10rem]">
	<div class="mx-auto md:w-40%">
		<p class="text-2xl text-center">Sign up for the newsletter</p>
		<p class=" text-center mt-3">
			Stay up to date with the roadmap progress, announcements and exclusive discounts feel free to
			sign up with your email.
		</p>
	</div>

	<div class="flex items-center mx-auto md:w-30% mt-8">
		<input
			type="email"
			placeholder="Enter your email"
			bind:value={email}
			class="w-full py-2 px-4 border border-gray-300 rounded-l focus:outline-none focus:border-blue-500"
		/>
		<button
			class="py-2 px-4 bg-blue-500 text-white rounded-r hover:bg-blue-600 focus:outline-none"
			on:click={onSubscribe}>Subscribe</button
		>
	</div>
	{#if emailError}
		<div class=" flex flex-1 justify-center text-red-500 mt-2">
			<p>Please enter a valid email address.</p>
		</div>
	{/if}
	{#if successEmail}
		<div class=" flex flex-1 justify-center text-green-500 mt-2">
			<p>Thank you for subscribing!</p>
		</div>
	{/if}

	<div class=" flex flex-1 justify-center mt-3">
		<p class=" text-xs">
			We care about the protection of your data. Read our <span class="font-bold underline"
				>Privacy Policy.</span
			>
		</p>
	</div>
</div>
