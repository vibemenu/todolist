<script>
  import { getSettings } from "./App.svelte";
  const settings = getSettings();
</script>

<div class="form-control">
  <label class="input-group">
    <span>Placeholder text</span>
    <input
      type="text"
      bind:value={$settings.placeholderText}
      class="input input-bordered"
    />
  </label>
</div>
