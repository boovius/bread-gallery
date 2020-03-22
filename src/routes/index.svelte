<style>
	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}
</style>


<script>
  import Tile from '../components/Tile.svelte';
  import Masonry from '../components/Masonry.svelte';
  let breads = ['Rye bread', 'Wheat Bread', 'Sourdough', 'Challah', 'Brioche', 'Croissant', 'Baguette', 'Integral', 'Semolina', 'Tordu', 'Fendu'];
</script>

<svelte:head>
	<title>Bread Gallery</title>
</svelte:head>

<h1>Bread Gallery</h1>
<Masonry>
  {#each breads as bread, i}
    <Tile index={i + 1} breadName={bread} />
  {/each}
</Masonry>
