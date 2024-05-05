<script>
	import headshot from '$lib/images/KyleGibbsProfile.png';
	import { Timeline } from 'svelte-vertical-timeline';
	import ImageBox from '../lib/components/ImageBox.svelte';

	let imageUrls = {
		batman: 'https://cdn.mobygames.com/06e74fd8-abb3-11ed-9e18-02420a00019a.webp'
	};
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section class="flex flex-row content-center items-center">
	<div class="flex-1 text-center text-lg flex-col">
		<h1>Kyle Gibbs</h1>
		<h4>Software Engineer for Video games</h4>
	</div>

	<span class="flex-1 text-center text-lg pb-5 rounded">
		<picture>
			<ImageBox title="Kyle Gibbs" rounded={true} imageUrl={headshot} imgWidth={400} />
		</picture>
	</span>
</section>

<section class="flex flex-row justify-center items-center">
	<div class="flex pb-10 -ml-10">
		<h3 class="section-header">Commercial Games</h3>
	</div>

	<ImageBox title="Batman" imageUrl={imageUrls.batman} imgWidth={300}></ImageBox>
</section>
