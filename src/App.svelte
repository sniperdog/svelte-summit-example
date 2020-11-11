<script>
	import { cats } from "./cats.js"
	import { tags } from "./tags.js"
	
	let currentTag = ""
	function setTag(tag) {
		if (currentTag === tag) {
			currentTag = ""
		} else {
			currentTag = tag;	
		}
	}
</script>

<main>
	<header>
		<h1>Cat Finder</h1>
	</header>
	<h2>Search by</h2>
	<div class="tags">
		{#each tags as tag}
			<span on:click={() => setTag(tag)} class="tag {currentTag === tag ? 'current' : ''}">{tag}</span>
		{/each}
	</div>
	<div class="cats">
		{#each cats as cat}
			{#if currentTag === "" || cat.tags.includes(currentTag)}
				<div class="cat" style="background: center / cover url({cat.imageLink})"></div>
			{/if}
		{/each}
	</div>
</main>

<style>
	.current {
		color: #ffffff !important;
		background: #009B3E !important;
	}
	.cat {
		margin: 0 auto 16px auto;
		width: 328px;
		height: 200px;
		filter: drop-shadow(0px 0px 2px rgba(0,0,0,0.14)), drop-shadow(0px 2px 2px rgba(0,0,0,0.12)), drop-shadow(0px 1px 3px rgba(0,0,0,0.2));
		border-radius: 8px;
	}
	.tags {
		height: 46px;
		width: 100%;
		white-space: nowrap;
		overflow-x: auto;
		margin: 8px 16px 16px 16px;
	}
	.tag {
		background: #E9E9E9;
		border-radius: 4px;
		padding: 4px 8px;
		margin-right: 8px;
		user-select: none;
	}

	header {
		text-align: center;
		background: #FFFFFF;
		box-shadow: 0px 0px 2px rgba(0,0,0,0.14), 0px 2px 2px rgba(0,0,0,0.12), 0px 1px 3px rgba(0,0,0,0.2);
	}

	h1 {
		margin: 0;
		padding: 12px 0;
		font-weight: 600;
		font-size: 40px;
		line-height: 110%;
	}

	h2 {
		font-weight: 600;
		font-size: 14px;
		line-height: 110%;
		text-transform: uppercase;
		color: rgba(0,0,0,0.54);
	}
</style>