<script>
	import SAPI from '$lib/searchAPI/searchAPI.svelte'
	import Content from '$lib/content/Content.svelte';
</script>

<svelte:head>
	<title>Wiki RESTful test</title>
</svelte:head>

<section>
	<Content />
</section>

<section class="container sapi" align="center">
	<SAPI />
</section>

<section>
	<div class="container buttons">
		<div class="row">
			<div class="btn col-lg-6">
				<a href="/articles" class="btn btn-primary">
					Take me to all the articles
				</a>
			</div>
			<div class="btn col-lg-6">
				<a href="/new_article" class="btn btn-primary">
					Create a new article
				</a>
			</div>
		</div>
	</div>
</section>

<style>
	.buttons {
		align-items: center;
	}

	.sapi {
		margin: 180px auto;
	}
</style>
