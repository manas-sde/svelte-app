<div class='slider'>
<Slider
  bind:value
  min={-100}
  max={100}
  step={5}
  discrete
  tickMarks
  
/>
</div>

<pre class="status">Value: {value}</pre>
Value = 100

<script lang="ts">
  import Slider from '@smui/slider';

  let value = 0;
</script>

<style>
    .slider {
        width: 100%;
        float: center;
        outline: auto;
    }
</style>
