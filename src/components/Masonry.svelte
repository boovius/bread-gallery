<script>
    // Should take 3 params: minWidth, gap, as
    export let numCols = 6;
    export let minHeight = 150;
    export let gap = 10;
    let style;

    $: style = `
            grid-template-columns: repeat(${numCols},1fr);
            grid-template-rows: minxmax(${minHeight}px,auto);
            grid-gap: ${gap}px;
        `;
</script>
<style>
  .base {
    display: grid;
    grid-auto-flow: dense;
    background-color: #aaa;
  }
</style>

<div class="base" style={style}>
    <slot></slot>
</div>
