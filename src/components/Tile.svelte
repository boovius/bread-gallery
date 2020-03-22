<script>
  export let breadName;
    // Should take 2 params: x, y
  export let index = 1;
  let xSpan = index % 2;
  let ySpan = index % 3;
  console.log(xSpan);
  console.log(ySpan);

  let focused;

  function handleMouseOver(e) {
    focused = true;
  }

  function handleMouseLeave(e) {
    focused = false;
  }

    // styles
    let style;

    $: style = `
                overflow: hidden;
                position: relative;
                grid-row-end: span ${ySpan + 1};
                grid-column-end: span ${xSpan + 1};
              `;
</script>

<div style={style} on:mouseover={handleMouseOver} on:mouseleave={handleMouseLeave}>
  {#if focused}
    <figure class='overlay'>
      <img alt='bread' src='https://breadtopia.com/wp-content/uploads/2018/04/IMG_20180409_145806.jpg'>
      <figcaption>{breadName}</figcaption>
    </figure>
  {:else}
    <figure>
      <img alt='bread' src='https://breadtopia.com/wp-content/uploads/2018/04/IMG_20180409_145806.jpg'>
    </figure>
  {/if}
</div>

<style>
  figure {
    margin: 0;
    display: grid;
    grid-template-rows: 1fr 1fr 1r;
    grid-template-columns: 1fr 1fr 1r;
  }
  figure img {
    height: 100%;
    width: 100%;
    grid-area: 1/1/4/4;
  }
  figcaption {
    background-color: black;
    text-align: center;
    color: white;
    grid-row: 2/2;
    grid-column: 1/4;
  }
  .overlay {
    background-color: black;
    opacity: .7;
  }
</style>

