<script lang="ts">
	import '../app.postcss';

	import Header from '../lib/header.svelte';

	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });
</script>

<nav class="flex items-center justify-evenly flex-wrap p-6">
	<div class="w-full block flex-grow lg:flex lg:items-center lg:w-auto">
		<div class="text-sm lg:flew-grow">
			<a href="/" class="block mt-4 lg:inline-block lg:mt-0 hover:text-white mr-4">Home</a>
			<a href="/admin" class="block mt-4 lg:inline-block lg:mt-0 hover:text-white mr-4">URL Admin</a
			>
		</div>
	</div>
</nav>
<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-x-2 space-y-5">
		<Header />
		<main>
			<slot />
		</main>
	</div>
</div>
