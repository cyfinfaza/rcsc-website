<script>
	import HeaderWithImage from '../../components/HeaderWithImage.svelte';
	import Metadata from '../../components/Metadata.svelte';

	const fp = 12;
	const cp = 20;
	const bm = 13;
	function calcTotalPrice(n) {
		return Math.max(cp * Math.pow(n, Math.log((fp * bm) / cp) / Math.log(bm)), fp * n);
	}

	let numShirts = 1;
	let nthShirt = 1;
	let unitPrice;
	let totalPrice;
	let marginalPrice;
	$: unitPrice = calcTotalPrice(numShirts) / numShirts;
	$: totalPrice = calcTotalPrice(numShirts);
	$: marginalPrice = calcTotalPrice(nthShirt) - calcTotalPrice(nthShirt - 1);

	const ordinal = (n) =>
		({ one: 'st', two: 'nd', few: 'rd', other: 'th' }[
			new Intl.PluralRules('en', { type: 'ordinal' }).select(n)
		]);

	const isPositiveAndInteger = (n) => n > 0 && n % 1 === 0;
</script>

<Metadata
	title="T-Shirt Printing"
	description="Shirts as low as $12 per shirt, from the Ridge Comp Sci Club!"
	image="/images/PXL_20221013_192802342.jpg"
/>

<HeaderWithImage imageSrc="/images/PXL_20221013_192802342.jpg"
	>Shirts as low as $12/shirt</HeaderWithImage
>
<p>
	Need a custom printed shirt for yourself or your club? <br />
	We can make it for you, often for
	<strong> cheaper than CustomInk or other online platforms</strong>! <br />
	Get your shirts &rarr; contact us at
	<a href="mailto:shirts@ridgecompsci.club">shirts@ridgecompsci.club</a>
</p>
<h2>Benefits</h2>
<ul>
	<li>Cheaper than other methods</li>
	<li>See a sample shirt before you buy</li>
	<li>Easy mongraming</li>
	<li>No shipping, just pick up your shirts from us in school</li>
	<li>Support fellow school clubs!</li>
</ul>
<h2>Pricing</h2>
<p>
	Shirts start at <strong>${cp}</strong> for a single shirt, but the price can get as low as
	<strong>${fp} per shirt</strong> if you order more than one.<br />
</p>
<h3>How Bulk Pricing Works</h3>
<p>
	For every additional shirt you order between 1 and {bm} shirts, we reduce the price per shirt until
	it reaches ${fp}. For more than {bm} shirts, the price per shirt is ${fp}. <br />
	Don't want to order every shirt at once? With our pricing model, your first shirts will cost more than
	the base price, but the ones you order later will cost less than the base price, making everything
	average out. <br /> <strong>See the numbers for yourself below.</strong>
</p>
<h3 id="pricecalculator">See how much you'll pay</h3>
<p>
	Enter number of shirts: <input type="number" bind:value={numShirts} min="1" step="1" />
	&rarr;
	{#if isPositiveAndInteger(numShirts)}
		Base Price: <strong>${unitPrice.toFixed(2)} per shirt</strong>, Total Price:
		<strong>${totalPrice.toFixed(2)}</strong>
	{:else}
		Invalid number of shirts
	{/if}
</p>
<p>
	How much will I pay for the <input
		type="number"
		bind:value={nthShirt}
		min="1"
		step="1"
	/>{ordinal(nthShirt)} shirt? &rarr;
	{#if isPositiveAndInteger(nthShirt)}
		<strong>${marginalPrice.toFixed(2)}</strong>
	{:else}
		Invalid number of shirts
	{/if}
</p>
<h3>Disclaimer</h3>
<p>
	Some factors could result in your price being greater than the base price, including but not
	limited to:
</p>
<ul>
	<li>Many colors in your design</li>
	<li>Monogramming</li>
</ul>
<h2>How to order or ask questions</h2>
<p>
	If you are interested in purchasing a shirt for yourself or ordering shirts for your club, you can
	either:
</p>
<ul>
	<li>Email us at <a href="mailto:shirts@ridgecompsci.club">shirts@ridgecompsci.club</a></li>
	<li>Come to one of our meetings</li>
	<li>Talk to an officer directly (if you know one)</li>
</ul>

<style>
	input[type='number'] {
		width: 3em;
	}
</style>
