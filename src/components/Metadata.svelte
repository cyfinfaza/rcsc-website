<script>
	export let title;
	export let description;
	export let image;
</script>

<svelte:head>
	<title>{title ? title + ' | ' : ''}Ridge Comp Sci Club</title>
	<meta property="og:title" content={(title ? title + ' | ' : '') + 'Ridge Comp Sci Club'} />
	{#if description}
		<meta name="description" content={description} />
		<meta property="og:description" content={description} />
	{/if}
	{#if image}
		<meta name="image" content={image} />
		<meta property="og:image" content={image} />
	{/if}
</svelte:head>
