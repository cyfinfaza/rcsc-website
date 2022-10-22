<script>
	import HeaderWithImage from '../../components/HeaderWithImage.svelte';
	import Metadata from '../../components/Metadata.svelte';

	let numShirts = 1;
	let shirtPrice;
	$: shirtPrice = 25 - Math.min(numShirts - 1, 13);
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
	Shirts start at <strong>$25</strong> for a single shirt, but we support bulk pricing for larger orders.
	That way, you can get your shirts made locally with us, often for a much lower price than online alternatives!
</p>
<h3>How Bulk Pricing Works</h3>
<p>
	For every additional shirt in your order, we lower the base price by $1, until you reach 14
	shirts. That means shirts can cost as little as <strong>$12 per shirt</strong>!
</p>
<h3>Base price calculator</h3>
<p>
	Enter number of shirts: <input
		type="number"
		style="width: 4em;"
		bind:value={numShirts}
		min="1"
		step="1"
	/>
	&rarr;
	{#if numShirts >= 1 && parseInt(numShirts) == numShirts}
		Base Price: <strong>${shirtPrice} per shirt</strong>, Total Price:
		<strong>${shirtPrice * numShirts}</strong>
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
