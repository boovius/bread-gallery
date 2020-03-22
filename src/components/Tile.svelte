<script>
  export let breadName;
  export let breadImage = 'https://breadtopia.com/wp-content/uploads/2018/04/IMG_20180409_145806.jpg';
    // Should take 2 params: x, y
  export let index = 1;
  let xSpan = index % 2;
  let ySpan = index % 3;
  console.log('index', index + 1);
  console.log('xSpan', xSpan + 1);
  console.log('ySpan', ySpan + 1);

  let focused = false;

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
                grid-column-end: span ${xSpan + 1};
                grid-row-end: span ${ySpan + 1};
                background-image: url(${breadImage});
              `;
</script>

<figure class={focused ? 'overlay': ''} style={style} on:mouseover={handleMouseOver} on:mouseleave={handleMouseLeave}>
  <img alt='bread' src={breadImage}>
  {#if focused}
    <figcaption>{breadName}</figcaption>
  {/if}
</figure>

<style>
  figure {
    margin: 0;
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    display: grid;
    grid-template-rows: repeat(3, 1fr);
    grid-template-columns: repeat(3, 1fr);
  }
  figure img {
    height: 100%;
    width: 100%;
    grid-area: 1/1/4/4;
    visibility: hidden;
  }
  figcaption {
    background-color: black;
    color: white;
    text-align: center;
    height: 35px;
    grid-row: 2/2;
    grid-column: 1/4;
  }
  .overlay {
    background-color: black;
    opacity: .7;
  }
</style>

