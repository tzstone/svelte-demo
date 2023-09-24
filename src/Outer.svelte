<script>
  import Inner from './Inner.svelte'
</script>

<!-- on:message没有赋值->转发事件, on:click亦同  -->
<Inner on:message on:click></Inner>