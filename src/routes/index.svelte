<svelte:head>
	<title>Kokodokai</title>
</svelte:head>

<script context="module" type="text/javascript">
	import Title from '../components/Title.svelte';
					export async function preload({ params, query }) {
		return this.fetch(`index.json`).then(r => r.json()).then(posts => {
			return { posts };
		});
	}
</script>

<script>
	export let posts;
</script>

<Title title="Rise Above"}></Title>

<ul>
	{#each posts as post}
		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
		<li>
			<a rel='prefetch' href='{post.slug}'>
				{#if post.image}
					<figure>
						<span><img src="{post.image}" alt="" /></span>
					</figure>
				{/if}
				{post.title}
			</a>
		</li>
	{/each}
</ul>

<style lang="scss" type="text/scss">
	@import "./index.scss";

	$color: green;
	li a {
		color: $color;
	}
</style>




