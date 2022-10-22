<script>
	export let imageSrc;
</script>

<div class="container">
	<img src={imageSrc} alt="" />
	<h1 class="bigHeading"><slot /></h1>
</div>

<style lang="scss">
	div {
		display: flex;
		width: 100%;
		position: relative;
		overflow: hidden;
		border-radius: 12px;
		z-index: -1;
	}
	img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		position: absolute;
	}
	h1 {
		z-index: 10;
		padding: 12px;
		margin: 0;
		padding-top: 4em;
		width: 100%;
		background: linear-gradient(to bottom, rgba(0, 0, 0, 0.1) 0%, rgba(0, 0, 0, 0.3) 80%);
		text-shadow: 0 0 12px rgba(0, 0, 0, 0.8);
	}
</style>
