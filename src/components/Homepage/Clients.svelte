<script lang="ts">
	import GoogleLogo from '../../assets/GoogleLogo.png';
	import MicrosoftLogo from '../../assets/MicrosoftLogo.png';
	import SpotifyLogo from '../../assets/SpotifyLogo.png';
	import MailchimpLogo from '../../assets/MailchimpLogo.png';
</script>

<div class="flex flex-1 flex-col items-center mt-15">
	<div>
		<p class="text-2xl">You'll be in good company</p>
	</div>

	<div class="grid grid-cols-2 md:grid-cols-4 gap-2 mt-8">
		<img src={GoogleLogo} class="w-auto h-8" alt="" />
		<img src={MicrosoftLogo} class="w-auto h-8" alt="" />
		<img src={SpotifyLogo} class="w-auto h-8" alt="" />
		<img src={MailchimpLogo} class="w-auto h-8" alt="" />
	</div>
</div>
