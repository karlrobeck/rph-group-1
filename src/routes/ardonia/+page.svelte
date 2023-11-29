<script>
	import showdown from 'showdown';
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	const converter = new showdown.Converter();
	converter.setFlavor('github');

	let document;
	onMount(async () => {
		const res = await fetch(`${base}/ardonia.md`);
		document = converter.makeHtml(await res.text());
	});
</script>

<svelte:head>
	<title>Ardonia Blog</title>
</svelte:head>

<!-- Blog Article -->
<main class="w-full dark:bg-gray-900 min-h-screen h-full">
	<div class="h-full max-w-3xl px-4 pt-6 lg:pt-10 pb-12 sm:px-6 lg:px-8 mx-auto">
		<div class="max-w-2xl flex flex-col items-center">
			<div class="flex flex-col w-full">
				<a
					class="pb-4 inline-flex items-center gap-x-1.5 text-sm text-gray-600 decoration-2 hover:underline dark:text-blue-400 dark:focus:outline-none dark:focus:ring-1 dark:focus:ring-gray-600"
					href={base ? base : '/'}
				>
					<svg
						class="flex-shrink-0 w-4 h-4"
						xmlns="http://www.w3.org/2000/svg"
						width="24"
						height="24"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"><path d="m15 18-6-6 6-6" /></svg
					>
					Back to Blog
				</a>
				<!-- Avatar Media -->
				<div class="flex justify-between items-center mb-6">
					<div class="flex w-full sm:items-center gap-x-5 sm:gap-x-3">
						<div class="flex-shrink-0">
							<img
								class="h-12 w-12 rounded-full object-cover"
								src="https://scontent.fmnl25-3.fna.fbcdn.net/v/t39.30808-1/340242717_6033317763384716_670218383113599144_n.jpg?stp=dst-jpg_p200x200&_nc_cat=106&ccb=1-7&_nc_sid=5740b7&_nc_eui2=AeE7xeoyLJXSHoCVbO_GMFCgX5UiGWLoIgxflSIZYugiDMC-s3zt5gcVGn8RnpVPGq7YRqpHCmvLKPkavy5pCqeF&_nc_ohc=dbf0rXK1Hn0AX9wVm2p&_nc_ht=scontent.fmnl25-3.fna&oh=00_AfCsf6xWKEqxq5QxQ_QnSR3wCnRjXzcfg3k90xuHe7ZwrA&oe=656C56CC"
								alt="Ralph Ardonia"
							/>
						</div>
						<div class="grow">
							<div class="flex justify-between items-center gap-x-2">
								<div>
									<!-- Tooltip -->
									<div class="hs-tooltip inline-block [--trigger:hover] [--placement:bottom]">
										<div class="hs-tooltip-toggle sm:mb-1 block text-start cursor-pointer">
											<span class="font-semibold text-gray-800 dark:text-gray-200">
												Ralph Ardonia
											</span>
										</div>
									</div>
									<!-- End Tooltip -->

									<ul class="text-xs text-gray-500">
										<li
											class="inline-block relative pe-6 last:pe-0 last-of-type:before:hidden before:absolute before:top-1/2 before:end-2 before:-translate-y-1/2 before:w-1 before:h-1 before:bg-gray-300 before:rounded-full dark:text-gray-400 dark:before:bg-gray-600"
										>
											November 30, 2023
										</li>
									</ul>
								</div>
								<!-- Button Group -->
								<div>
									<a
										href="https://www.facebook.com/ralphlauren.ardona"
										target="_blank"
										type="button"
										class="py-1.5 px-2.5 inline-flex items-center gap-x-2 text-sm font-medium rounded-lg border border-gray-200 bg-white text-gray-800 shadow-sm hover:bg-gray-50 disabled:opacity-50 disabled:pointer-events-none dark:bg-slate-900 dark:border-gray-700 dark:text-white dark:hover:bg-gray-800 dark:focus:outline-none dark:focus:ring-1 dark:focus:ring-gray-600"
									>
										<svg
											xmlns="http://www.w3.org/2000/svg"
											width="16"
											height="16"
											fill="currentColor"
											class="bi bi-facebook"
											viewBox="0 0 16 16"
										>
											<path
												d="M16 8.049c0-4.446-3.582-8.05-8-8.05C3.58 0-.002 3.603-.002 8.05c0 4.017 2.926 7.347 6.75 7.951v-5.625h-2.03V8.05H6.75V6.275c0-2.017 1.195-3.131 3.022-3.131.876 0 1.791.157 1.791.157v1.98h-1.009c-.993 0-1.303.621-1.303 1.258v1.51h2.218l-.354 2.326H9.25V16c3.824-.604 6.75-3.934 6.75-7.951"
											/>
										</svg>
										Facebook
									</a>
								</div>
								<!-- End Button Group -->
							</div>
						</div>
					</div>
				</div>
				<!-- End Avatar Media -->
			</div>

			<!-- Content -->
			<div
				class="prose dark:prose-invert prose-img:rounded-md prose-img:h-60 prose-img:w-full prose-img:object-cover"
			>
				{#if document}
					{@html document}
				{/if}
			</div>
			<!-- End Content -->
		</div>
	</div>
</main>
<!-- End Blog Article -->
